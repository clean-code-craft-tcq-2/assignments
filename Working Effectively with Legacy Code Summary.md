### Working Effectively with Legacy Code

---

#### Reasons To Change

---

- Adding a Feature
- Fixing a Bug
- Improving the Design
  - One of the main reasons why many programmers don’t attempt to improve design often is because it is relatively easy to lose behavior or create bad behavior in the process of doing it.
  - Refactoring : The act of improving design without changing its behavior is called refactoring
- Optimizing Resource Usage
  - We’re going to keep functionality exactly the same when we make changes, but we are going to change something else. (resource used by the program, usually time or memory)

#### Putting It All Together

---

|                   | Adding A Feature | Fixing a Bug | Refactoring | Optimization |
| ----------------- | ---------------- | ------------ | ----------- | ------------ |
| Structure         | Changes          | Changes      | Changes     | -            |
| Functionality     | Changes          | Changes      | -           | -            |
| Resource Changes  | -                | -            | -           | Changes      |
| New Functionality | Changes          |              |             |              |

>In all four cases, we want to change some functionality, some behavior, but we want to preserve much existing behavior

> Preserving existing behavior is one of the largest challenges in software development. Even when we are changing primary features, we often have very large areas of behavior that we have to preserve.

#### Risky Change (Make changes and Preserve behavior,)

---

- What changes do we have to make?
- How will we know that we’ve done them correctly?
- How will we know that we haven’t broken anything?

>
>
>How much change can you afford if changes are risky?
>
>Avoiding or optimizing Change
>
>- If it’s not broke, don’t fix it.”
>- “What? Create another method for that? No, I’ll just put the lines of code right here in the method, where I can see them and the rest of the code. It involves less editing, and it’s safer
>- When people don’t make changes often they get rusty at it
>- Unfortunately, many teams live with incredible fear of change and it gets worse every day



####  Avoiding change is a bad thing, but what is  alternative?

#### Two major approaches to change a system.

----

- Edit and Pray 
  - working with **care**
- Cover and Modify
  - work with a safety net
  - Covering software entails writing **tests** for it. We can make changes to a piece of code and immediately determine whether the consequences were positive or bad if we have a good set of tests around it. We still take the same precautions, but thanks to the feedback we've received, we've been able to refine our approach.
  - testing to attempt to show correctness.”
  - testing to detect change
  - When you have tests around the areas in which you are going to make changes, they act as a software vise
    - It's like having a vise around our code when we have tests that detect change. The code's behavior has been set in stone. When we make adjustments, we may be confident that we are only altering one aspect of our behavior at a time. In a nutshell, we're in charge of our work.

-

#### How do we start making changes in a legacy project?

---

> It's usually a good idea to run tests on any modifications we make. We can introduce problems when we alter code; after all, we're all human. However, if we test our code before changing it, we'll be more likely to notice any faults we make.

>Dependency is one of the most critical problems in software development. Much legacy code work involves breaking dependencies so that change can be easier.



>The Legacy Code Dilemma :  When we change code, we should have tests in place. To put tests in place, we often have to change code



#### The Legacy Code Change Algorithm

----

- Identify change points.
  - I Don’t Understand the Code Well Enough to Change It, 
  - My Application Has No Structure.
- Find test points.
  - I Need to Make a Change. What Methods Should I Test?
  - I Need to Make Many Changes in One Area
  -  Do I Have to Break Dependencies for All the Classes Involved?
- Break dependencies.
  - How Do I Know That I’m Not Breaking Anything?
  - I Can’t Get This Class into a Test Harness,
  - I Can’t Run This Method in a Test Harness
  -  I Need to Change a Monster Method and I Can’t Write Tests for It.
  -   It Takes Forever to Make a Change
- Write tests.
  - I Need to Make a Change but I Don’t Know What Tests to Write,
- Make changes and refactor.
  - How Do I Add a Feature
  - This Class/Function  Is Too Big and I Don’t Want It to Get Any Bigger
  - I’m Changing the Same Code All Over the Place



