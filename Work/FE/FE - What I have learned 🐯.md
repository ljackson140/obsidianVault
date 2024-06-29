### Tan-stack
- Tan-stack is a better asynchronous state management for creating queries - API calls 
	-  Once we make an API call and retrieve the data successfully, TS Query manages the query caching with an identified key
	-  When data chan
	- ges, Tan-Stack needs to know to invalidate the corresponding query results to ensure fresh data is fetched when needed
		-  we provide the invalidation to other functions so that when we **ADD** new data => go invalidate the cache data and refetch to get the lastest
	- TS also gives us the option t0 handle the query via **onSucess** either to set a state to false or activating a snack bar to pop up when the API call was successful
	- TS provides us mutations which is typically used to create/update/delete data or perform server side-effect such as handling errors/success returned   
	- ![[Pasted image 20240629165617.png]]
	- The image above lets me know that once we create a new hub => invalidate the data in that key, if something changed refetch
		- The pageSize also acts as a key as well in which when I  switch pages in the table it will go and fetch the second set of data in the cache 
	- ![[Pasted image 20240629170228.png]]
	- For this example above we are using the onSuccessCallback to set our setters 
	- addHubMutation is our function that will take our request and make the POST to the BE
### Logical Nesting API 
- Refers to the organization and structuring of endpoints in a way that reflects the hierarchical relationships between resources
- This approach makes the API more intuitive and easier to understand
- Ex:
	- **GET /projects/{projectId}/tasks**: Fetch all tasks for a specific project.
	- **POST /projects/{projectId}/tasks**: Create a new task within a specific project.
	- **GET /projects/{projectId}/tasks/{taskId}**: Fetch a specific task within a project.
	- **PUT /projects/{projectId}/tasks/{taskId}**: Update a specific task within a project.
	- **DELETE /projects/{projectId}/tasks/{taskId}**: Delete a specific task within a project
### Tree shaking 
- It is an optimization technique used to reduce the size of a bundle 
- `tree-shaking`=> process of removing unused code which results in a more efficient and faster loading application  
- the index.js file acts as an entry point that re-exports 

