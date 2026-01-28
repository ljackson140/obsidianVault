
Today
- [ ] Fix PR comments 
- [ ] Excel File

Derived state:
	- Pros:
	- Cons: reduce needless re-rendering 

- The structure of Configurable components, the update methods and the data flow in the front end needs to be re-assessed to ensure that each component has a clear scope boundary.
- Furthermore, the independent component's responsibility with styling spacing should be made consistent at a component type level.

so you'd pass the object (indexedAuthorisationComments) to the child component (AuthorisationComment) for their usage.
It'd also take the function (updateDisciplineAuthCommentValue, deleteDisciplineAuthCommentValue and insertDisciplineAuthCommentValue) so that it could call it with the updated object.

-Needs some refactoring as I think these functions shouldn't be manipulating data at this level.  
-The children components can update the records as required and pass up their own modifications. 
-The parent shouldn't be concerned with what needs to be done, only that the data from the child needs to be merged in with all other authorization comments.

US - Remove CSP
- [x] AC1
- [x] AC2
- [x] AC3
- [x] AC4
- [x] AC5a and AC5b
- [x] AC6
- [x] AC7a and AC7b
- [x] AC8
- [x] AC9
- [x] AC10
- [x] AC11