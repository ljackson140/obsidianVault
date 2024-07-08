
### Development Best Practices Checklist

#### General Code Quality

- [ ] **Catch Hard Coded Data**
- [ ] **Deconstruct Props**
- [ ] **Ensure Correct Component Rendering**
- [ ] **Avoid Unnecessary Properties** for any component
- [ ] **Use CamelCase for Method Names,  Variables** `const defaultValues = {}`
- [ ] **PascalCase for Interfaces, Files and Functions** `function ReturnPermitForm`
- [ ] **Refactor Functions with Multiple Return Statements** to Smaller Components If Necessary
- [ ] **Consider Consolidating Multiple Interfaces** into a Base Interface
- [ ] **Ensure Non-Nullable Object Checks** (e.g., `sites!.data`)
- [ ] **Avoid Unnecessary Constants Referencing Props** (e.g., `const series = props.series;`)
- [ ] **Use Objects or Constants Instead of Strings** for static data
- [ ] `Id` should always be an `int` in any data structure
- [ ] Ensure local logic is in the relevant file - Parent doesn’t need child logic in its level

#### CSS and Styling

- [ ] **Avoid `!important` in CSS** Unless Absolutely Necessary
- [ ] **Use `rem` Over `px` for Spacing Elements** to Ensure Consistency with Font Size Changes

#### File and Code Organization

- [ ] **Move Functions Out of Constant Files** into Helper Files
- [ ] **Consistently Format All Files**
- [ ] Files should be PascalCase `ReturnPermitForm`

#### TypeScript and Type Safety

- **Avoid Using `any` Type**; Ensure Typed Definitions

#### State Management

- **Consider `useReducer` for Multiple State Management** (especially for multiple states)
- Using `useContext` to pass data to the parent is a No Go  

#### Testing

- **Avoid "data-testid" in Test Files**
- **Ensure Comprehensive Test Coverage** for Both Frontend and Backend

#### Performance and Optimization

- **Use String Interpolation** Instead of String Concatenation (e.g., `${option.givenName} ${option.givenSurname}`)
- **Refactor Duplicated Functions** to Use Generics or Shared Functions

#### API and Data Handling

- **Check Payload Requests for Duplicated Fields**
- **Reuse Existing Interfaces** (e.g., `IOption`) for Similar Data Structures `Checkboxes only need Id and Value`
- **Remove Static Data from Reusable Components**; **Pass Data as Props from Parent Components to the child**

#### Miscellaneous

- **Understand and Be Able to Explain the Code** to Reviewers
- **Prefer `useQuery` Over Promises** for Better Error Handling and Lifecycle Management
- **Pass Required Props Explicitly** to Components (e.g., Textboxes)
- **Use Strict Equality (`===`)** Instead of Loose Equality (`==`)
- **Prioritize Validation Checks** Based on Common and Extensive Criteria

