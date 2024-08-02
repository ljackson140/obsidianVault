31/07/2024
- [x] Finalise button
- [ ] Stop the pre-populating 

30/07/2024
- [x] Sprint Review
- [x] Sprint Retro
- [x] Refactor frontend  

29/07/2024
- [x] Fix bugs 

26/07/2024
- [x] Go over US and breakdown task
- [x] Add button at empty state

25/07/2024
- [x] Practice AZ900
- [x] Fix Comments
- [x] connect medicare to mygov
- [x] Call opticomm

24/07/2024
- [x] First bug not able to replicate, tried locally, dev and test 
- [x] 2nd bug get all roles including guest
- [x] 3rd bug 
- [x] 4th bug
- [x] Call Superloop
- [x] Check with Nathaniel on the building 
- [x] Pick up internet modem
- [x] Pay tech fee and book them again 

18/07/2024
- [x] Investigate story
- [x] Create branch
- [x] start implementation Identify either its FE or BE changes 
- [ ] Testing 
- [x] Ac1
- [x] Ac2
- [x] Ac3

17/07/2024
- [x] Meetings
- [x] Fix PR comments
- [x] Pick up new story
16/07/2024
- [x] catch up with carmen  
- [x] rebase maybe 
- [x] meetings
- [x] refactor func
15/07/2024
- [x] Fix TabOwner to SME
- [x] Removed duplicate Spec
- [x] Removed Comments and white spaces 
- [x] abduh question [nathan]
- [x] Test Case
- [x] Refactor logic 
12/07/2024
- [x] Get user Name
- [x] Get role
- [x] Get disciplines
- [x] Update HTML
11/07/2024
- [x] Refactor Email
- [x] Include template 
- [x] Test BE Case
10/07/2024
- [x] Backend Email and send 

09/07/2024
- [x] Pay off Electricity Bill
- [x] Get Email
- [x] Sign docs
08/07/2024
  - [x] Go over US
  - [x] Start US
06/07/2024
- [x] React Advance Playlist
- [x] Practice AZ-900 - meaning of the words
- [x] Order gas from Origin
- [ ] Find good landscaper/plumber to fix water build up

05/07/2024
  - [x] Hubs Bugs
	- [x]  Wrong Hub Dialog being shown when creating a new hub -> select a hub and click the Add button, it shows "Update Hub" instead of "New Hub.
	- [x] Page navigation not working
	- [x] When creating a new hub with a duplicate name, the dialog closes with no error being shown.
	- [x] Cannot delete multiple hubs.
	- [x] Edit dialog doesn't prompt when double-clicking on a hub.
	- [x] UI change on Add New Hub dialog.

1-07-2024
- [x] Innovation project meeting
- [x] Practice AZ-900
	- [x] Create quiz in MS Forms
- [x] Go over what I have learned for FE
- [x] PI Preparations
	- [x] Listen
	- [x] Ask Questions 

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

28-06-2024
- [x] Check PRs and ask questions/add suggestions
- [x] Go over what I have learned for FE
- [x] Go over what I have learned for BE
- [x] Go over PowerPoint Slide 4-6
- [x] Get Burrito
- [x] <span >Continue AZ-900 Course and Practice </span>
- [x] PI Planning Meeting
- [x] Check-in with Morris