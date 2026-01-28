Types of design Patterns:
1. **<font color="#00b0f0">Creational Patterns</font>**
	- Provide object creation mechanisms that increase flexibility and reuse of existing code
2. **<font color="#e36c09">Structural patterns</font>** 
	- Explain how to assemble objects and classes into larger structure, while keeping these structures flexible and efficient 
3. **<font color="#00b050">Behavioral Pattern</font>**
	- Take care of effective communication and the assignment of responsibilities between objects

Design patterns are identified within LAMS:

 -  **<font color="#e36c09">Repository Pattern</font>**: 
   - Used to abstract the data access layer and provide a clean separation between the data access and business logic.
   - Example: `IRepository<ApprovalRequestEntity>`, `IRepository<AuthorisationComment>`, etc.

* ***<font color="#00b050">Command Pattern</font>**:
   - Encapsulates a request as an object, thereby allowing for parameterization and queuing of requests.
   - Example: `DistributeApprovalRequestCommandHandler`, `AuthoriseDisciplineHandler`.

-  **<font color="#00b050">Specification Pattern</font> (NOT Purely Behavioral)**:
   - Encapsulates the logic for querying data in a reusable and composable manner.
   - Sometimes considered a **behavioral pattern** because it defines **business rules** for object selection.
	   - more commonly classified as a **domain-driven design (DDD) pattern** or **architectural pattern**, as it helps define **rules and constraints** for business logic rather than directly influencing behavior.
   - Example: `GetApprovalRequestWithInclusionSpecification`, `GetApprovalRequestByIdSpecification`.

-  **<font color="#e36c09">Decorator Pattern</font>**:
   - Adds behavior to objects dynamically without altering their structure.
   - Example: Extension methods like `CreateHistoryRecord`, `GetDistributeHistoryContent`.

- **<font color="#00b050">Observer Pattern</font>**:
   - Defines a one-to-many dependency between objects so that when one object changes state, all its dependents are notified.
   - Example: Notification services (`INotificationService`, `IPushNotificationService`, `IEmailService`).

- **<font color="#00b0f0">Factory Pattern</font>**:
   - Provides an interface for creating objects in a superclass but allows subclasses to alter the type of objects that will be created.
   - Example: The use of `IMapper` for mapping objects.

These design patterns help in making the application more modular, maintainable, and scalable.