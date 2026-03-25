### New Form Architecture: What Changed and Why It's Better
The Old Architecture (what was replaced)
Previously, discipline form state lived entirely inside ApprovalRequestContextProvider:

- `dirtyTabs, allTrackingComments, allAuthorisationComments` — flat maps keyed by discipline ID.
- Every child component (e.g. `TrackingComments`) called `updateAllTrackingComments` directly any time a field changed.
- There was no `FormProvider` scoped to a discipline — no react-hook-form ownership, no field arrays, no unified validation surface.
- Dirty state was a boolean flag manually toggled in the AR context.
- There was no snapshot mechanism, so navigating away and back lost any unsaved work.

The New Architecture
The new system introduces three coordinated layers:

### Layer 1 — Per-Discipline `FormProvider (DisciplineTabFormWrapper)`

Each discipline route now gets its own `useForm<DisciplineFormValues>()` wrapped in a `FormProvider`. This means:

- `TrackingComments` and `AuthorisationComments` use `useFormContext` / `useFieldArray` — they read/write directly into the form state rather than imperatively calling context updaters. Updates are atomic, reversible, and tracked by react-hook-form's reconciler.
- `formState.isDirty` is computed automatically from the initial/current value diff — no manual flag toggling.
- `handleSubmit` validates the whole discipline form before a save, giving a single validation boundary per discipline.


### Layer 2 — `FormProviderRegistry` (Zustand store + context)

The `form-provider-registry.store.ts` coordinates all mounted and unmounted discipline forms simultaneously:

| **Concern**           | **Mechanism**                                                                                         |
| --------------------- | ----------------------------------------------------------------------------------------------------- |
| Live form access      | `handles: Map<disciplineId, DisciplineFormHandle>` — mutable refs outside Zustand state, never cloned |
| Unmounted form memory | `snapshots: Map<disciplineId, DisciplineFormSnapshot>` — captures `isDirty` + `values` on deregister  |
| Reactive dirty signal | `dirtyRevision: number` — the only Zustand reactive field; bumped on every dirty transition           |

The key design decision — keeping `handles` and `snapshots` as plain `Maps` outside Zustand reactive state — means react-hook-form references are never serialised, cloned, or compared by Zustand, avoiding subtle stale-closure bugs.

### Layer 3 — Snapshot Lifecycle (navigate away → come back)

The wrapper's cleanup effect calls `registry.deregister(disciplineId)`, which:

1. Reads `valuesRef.current` (a `useRef` mirror kept fresh by `disciplineForm.watch()`) — reliable even after react-hook-form tears down its own internals during unmount.
2. Stores a `DisciplineFormSnapshot` with the form's last known values and dirty flag.

On re-mount, `registry.getSnapshot(disciplineId)` is called before `useForm()` — the form is seeded with the snapshot's `values` as `defaultValues`, restoring unsaved edits transparently. The snapshot is then deleted on `register()`.

### Layer 4 — Discipline-Scoped Navigation Blocker

`discipline-form-navigation-blocker.component.tsx` uses `useBlocker(isDirty)` from react-router, scoped to the **discipline form's dirty state**. This is distinct from the global `BlockNavigationModal` (AR-level navigation). The user gets a Save / Discard prompt specifically when leaving a dirty discipline tab, before the route transition completes.

Concrete Improvements:

| Problem (old)                                                                                            | Solution (new)                                                                                          |
| -------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| Navigating away from a dirty discipline tab silently discarded all edits                                 | Snapshot stored on unmount; values restored on re-mount                                                 |
| Any field change required manual calls to `updateAllTrackingComments` / `updateAllAuthorisationComments` | `useFieldArray` / `useFormContext` handle all mutations; sync to AR context is a thin `useWatch` bridge |
| `isDirty` was a manually-set boolean flag, easy to desync                                                | Derived automatically by react-hook-form from initial vs current values                                 |
| No navigation guard for dirty individual discipline tabs                                                 | `DisciplineFormNavigationBlocker` (discipline-scoped `useBlocker`)                                      |
| Validation was Yup-only, applied after reading flat maps                                                 | handleSubmit runs react-hook-form field-level validation before any mutation                            |
| `submit()` for the active discipline required threading values through the AR context                    | `registry.submitActiveDiscipline()` calls `handle.submit()` on the first dirty mounted form directly    |
| Multiple AR context state slices duplicated per-discipline data                                          | Each discipline owns its form; only the minimum bridge data flows to AR context for backward compat     |

**Current State: Mid-Migration**

The architecture is intentionally layered in transition. The new registry is fully operational for lifecycle, snapshots, navigation blocking, and per-discipline `FormProvider` ownership. The following bridges still run the old paths for backward compatibility:

- `useWatch` effects in `DisciplineTabFormWrapper` still sync to `allTrackingComments` / `allAuthorisationComments` so `saveDisciplineTabs` (in AR context) continues to work unchanged.
- `Jotai` atoms (`isTrackingCommentUpdatableAtom, isAuthorisationCommentUpdatableAtom`) are set from isDirty to gate `saveDisciplineTabs` and `authoriseDisciplineHandler`.
- `useIsARDirty()` (`use-is-ar-dirty.hook.ts`) still reads `dirtyTabs` from AR context, not `useRegistryDirtyRevision()` — the new hook is exported and ready but not yet wired in.
- `registry.submitActiveDiscipline()` is defined but not yet consumed by any save path.

The natural next steps of the migration would be: route `saveDisciplineTabs` through `registry.submitActiveDiscipline()`, switch `useIsARDirty` to read `useRegistryDirtyRevision()`, and retire the `dirtyTabs` / `allTrackingComments` / `allAuthorisationComments` maps from `ApprovalRequestContextProvider`.