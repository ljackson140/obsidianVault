### API Responses
- Delete (DELETE) responses should be:
	- 200 OK
	- 202 Accepted
	- 204 No content
- Created (POST):
	- 200 Ok
	- 201 Created
	- 202 Accepted: used in long-running operations
	- 204 No content: used for successful requests that do not need to return a resource
	- 422 Unprocessable Entity: server understands the content type of the request entity, but was unable to process the contained instructions i.e no SMES
- Updated (PUT):
	-  200 OK
	- 202 Accepted
	- 204 No content
	- **401 Unauthorized**: Indicates that the request requires user authentication
	- **403 Forbidden**: Indicates that the server understands the request but refuses to authorize it
	- **404 Not Found**: Indicates that the server cannot find the requested resource
	- 422 Unprocessable Entity: server understands the content type of the request entity, but was unable to process the contained instructions i.e no SMES
### Escape Hatch
- Escape hatches provide a way to handle exceptional cases or perform advanced operations that are not directly supported by the standard APIs or language constructs
- Basically in my validator I have an rule that checks if the user is the owner of the link and that returning “Admin can override” is the escape hatch 

### Key Changes:

1. **Replaced `ForEach` with `foreach`**: This allows for proper asynchronous handling within the loop.
2. **Used `continue` instead of `return`**: In the `AddDisciplineTrackingComment` method, use `continue` to skip to the next iteration instead of breaking out of the method altogether.

### Foreach vs x.foreach:

- **`foreach` loop**: Ensures that the asynchronous operations are awaited properly.
- **Task Continuation**: The `continue` keyword is used in place of `return` to move on to the next item in the loop if an item is added, ensuring that the loop continues processing other items.

This refactor should prevent the issues you've been encountering with task management and ensure that all operations are completed as expected.

### inner/outer functions

### db querying 
- loops and joins 
- Questions to ask when querying the db:
	- do i have to join alot of tables?
	- can I do this outside of a loop?
- If i am only checking to see if any items are returned => use a boolean instead of a list then checking if that list has any items 
- In memory => IEnumerable 
- Only database side => IQueryable 
- AsNoTracking => only good to track if the entity change  else if it is used multifle times might be best to set the spec to false 

### Modifiers
Sealed: 
- On a class that implements security features, so that the original object cannot be "impersonated".
    
-  More generally, I recently exchanged with a person at Microsoft, who told me they tried to limit the inheritance to the places where it really made full sense, because it becomes expensive performance-wise if left untreated.  
    The sealed keyword tells the CLR that there is no class further down to look for methods, and that speeds things up.
- In most performance-enhancing tools on the market nowadays, you will find a checkbox that will seal all your classes that aren't inherited.  Be careful though, because if you want to allow plugins or assembly discovery through MEF, you will run into problems.