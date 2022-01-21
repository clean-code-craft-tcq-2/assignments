### Unit Test

---

- Test specific aspects of a functionality
- Execute rapidly
- Independent of each other
- Independent of the surrounding environment
- Independent of execution order
- Automated

#### Value-based vs. state-based vs. interaction testing

---

- Value-based testing checks the value returned from a function
- State-based testing is about checking for noticeable behavior changes in the system under test, after changing its state.
- Interaction testing is testing how an object sends messages (calls methods) to other objects



#### External Dependency and Unit Test

---

> An external dependency is an object in your system that your code under test interacts with and over which you have no control. (Common examples are file systems, threads, memory, time, and so on.)

#### Inherent challenges in testing dependent objects

---

- Objects dependent on ephemeral objects produce unpredictable behavior

- User Interfaces, Databases and the like are inherently ephemeral

- How do you test that your object interacts with other objects correctly?

  

##### Stub

----

**A** **stub is a controllable replacement for an existing dependency** **(or** **collaborator) in the system. By using a stub, you can test your code without** **dealing with the dependency directly**

##### Mock

---

Complex collaborator interactions cannot be captured with a simple stub 

Defining interaction testing using  Mock Object

> A Mock Object is a fake dependency or stub  that verifies that the code being tested interacts with its collaborator properly.
>
> A mock object is a fake object in the system that decides whether the unit test has passed or failed. It does so by verifying whether the object under test called the fake object as expected. **There’s usually no more than one mock per test**.
>
> - The test tells the mock
>   - The expected calls
>   -  In the expected order
>   - What to return



###  TDD

---

-

- Is a programming practice

- Unit tests are written before the domain code
- Write a test that fails
- Write code to make the test pass
- Refactor
- Unit Tests and Refactoring are the tools of TDD



### The Benefits of TDD

---

- TDD ensures quality code from the start. Developers are encouraged to write only the code needed to make the test pass and thus fulfill the requirement. 
- Whether by design or by coincidence, most TDD practitioners write code that follows the SOLID principals
- TDD ensures a high degree of fidelity between the code and the business requirements.
- If your requirements are written as tests, and your tests all pass, you can say with a high degree of confidence that your code meets the needs of the business
- TDD encourages the creation of simpler, more focused libraries and APIs
- TDD encourages communication with the business. To create these tests, you are encouraged to interact with the business users. This way, you can make sure that the input and output combinations make sense, and you can help the users understand what they are building.
- TDD helps keep unused code out of the system. Most developers have written applications in which they designed interfaces and wrote methods based on what might happen. This leads to systems with large parts of code or functionality that are never used. This code is expensive. TDD helps keep this parasite code out of your system.
- TDD provides built - in regression testing. As changes are made to the system and your code, you always have the suite of tests you created to ensure that tomorrow ’ s changes do not damage today ’ s functionality.
- TDD puts a stop to recurring bugs, With TDD, as soon as a defect is reported, a new test is written to expose it. When this test passes, and continues to pass, you know the defect is gone for good
- When developing applications with testability in mind, the result is an architecture that is open, extensible and flexible. Dependency Injection  is a key component of both TDD and a loosely coupled architecture

### The Rules of TDD

---

- You are not allowed to write any production code until you have first written a failing unit test.
- You are not allowed to write more of a unit test than is sufficient to fail – and not compiling is failing
- You are not allowed to write more production code than is sufficient to pass the currently failing unit test

### TDD Steps

---

- **Write** a test.

- **Run** the test. It **fails to compile** because the code you're trying to test doesn't even exist yet! (This is the same thing as failing.)

- **Write a bare-bones stub** to make the **test compile**.

- Run the test. It should **fail**. (If it doesn't, then the test wasn't very good.)

- **Implement the code** to make the test pass.

- Run the test. It should **pass.** (If it doesn't, back up one step and try again.)

- Start over with a new test!

### When We Should Not Use TDD

---

- When Requirements are Volatile and Fuzzy
- When some parts of project are so simple, small, or less complex where complexity and risks are low
- TDD won’t help in getting a good architecture
  - If you are faced with fundamental decisions about frameworks, libraries, technologies, or architecture patterns, TDD will not help you
- The project is short, simple and straight-forward

### Why Developers Don’t Use TDD

---

- "Management Doesn’t Allow Us”
-  “Not Enough Time to Write Tests”
- “My Team Disagrees on Whether We Should Use TDD"
- “Return on Investment in TDD Isn’t Proven”
- “We Tried but It Didn’t Work”
- “Slow Build Process”
- “I Don’t Know All the Requirements Upfront to Write All Tests”



### How to Succeed With TDD

---

- Make each test very small and focused.
- Avoid making tests depend on each other, either explicitly or implicitly
- Make each test express its intent very clearly.
- Pay attention to failure messages. Make each failure message as helpful for diagnosis as you can.
- Involve as little of the system as you possibly can in each test

### TDD - Embedded System Constraints

---

- Development speed
  - when the target for test execution is not the same as the host for developing software, a delay is introduced into development
- Memory footprint
  - Tests and the testing framework are added to the program code residing in target memory
- Cross-compilation issues
  - Difference in processor architecture or build tool chain
- Hardware dependencies
  - External dependencies, like hardware interaction, complicate the automation of tests. Concurrent Hardware





