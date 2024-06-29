### Libraries Backend: (View Delete Link PR for a refresher)
#### NSubstitute:
	- Basically [substitutes] the original class or interface that you are testing 
	- mocks are strict by default 
#### Moq:
	- typically set up your mock objects using methods like Setup(), Returns(), Verifiable(), etc. 
		This can sometimes lead to more verbose code.
	- need to explicitly  configure them to be strict 
	
#### New Feature:
	- Ensure that theirs a Validator 
	- Ensure that the validator tests all of the AC's 
	- Ensure that theirs a test for the handler 

### Starting BE Test
#### Guides:
	Handler:
	1. Import the necessary Repositories, services and variables etc that you will need to mock the data 
	2. Mock the request and handler => the mock will return your type with the provided variables 
	3. create the functions that will be testing the mocked data => Arrange, Act and Assert
	
	Validator:
	1.Import necessary Repos, services and generated variables that you may need. 
	2. Mock the data within this you will be mocking the return type or objects 
	3. create functions to test each rule => the request for each rule will be different as you are passing in different args
	
#### Tips:
	- When you have a validator with rules => make sure each test covers each rule etc (The rules are mainly taken from the US)
	- Use validator to format text (Constants.ErrorMessage.GenericDoesNotExistMessage)
	- 