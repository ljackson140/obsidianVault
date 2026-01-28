### Libraries Frontend: (View Delete Link PR for a refresher)
#### MSW (Mock Service Worker):
	- Need api handler (mock api call for test)
	- setup handler for server 
#### Vitest:
	- npm run test (Runs all test)
	- npm run test [Enter file] (will run the specified test file )
	Dubugging:
		1. import { debug } from 'vitest-preview'
		2. Add [debug();] where you want to see the changes
		3. npm run test:preview 
		4. Run debug in VS Code
		5. now wait 			
		
#### Testing-Library:
	- queryBy = when we want to ensure an element is not [present] in the [DOM], we can make use of the [queryBy]
	- getBy = when we know an element is present in the [DOM]
	- findBy = waits for the element to appear in the DOM due to its [asynchronus] nature

### When testing ensure you have breakpoints in all of the files associated with the failing component 
- why is it failing?
- is it configured correctly?
- do you need to mock the data, if yes use either mockContext 
- think of everything that is associated with the component 
- How does the rendering occur?

### Starting FE Test
Guides:
	- Testing API Error Response [Scenario = Distributing a Blasting AR that has no SMEs in its disciplines thus returning an error that we show as an banner error]
	1. First we want to mock our API calls => get our data which is mocked (ensure correct values are used for our scenarios)
		1.1. if its more than 1 call in our case which is GET and PUT, we would also mock the `response and status` 
	2. Mock our routes; path = path to the page, element =  element/component that will be rendered, children = it is a child of the parent component and shares the same path
	3. Render our component with the necessary wrapperProps => mockRouterConfigProps, mockARProps and mockAuthProps
	4. Mocking our handlers = since our scenario is creating an AR we need to => identify the components and APi related to creating an AR 
		i.e. handlers and data since to create an AR we need the default_work_categories to include our type of AR (Blasting), update our default_work_sub_categories 
		as its the child and has to be mapped to the parent => we now create our work category response that will be used in the handler for workcategoryHandler 			
		- lookupHandler will also be updated to return the lookupResponse that we mocked (which is also needed for an AR)
	 5. Once all of the relevant APIs and data has been mocked we can now test to see if it is rendering correctly then perform the necessary logic to check for text, fireEvents etc

### Tips
- 