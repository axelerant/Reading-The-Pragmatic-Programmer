# A Pragmatic Approach

- The Essence of Good Design
- DRY - The Evils of Duplication - avoid duplication of information.
- Orthogonality - avoid splitting one piece of knowledge across multiple system components.
- Reversibility - how to make our applications relevant to changing environment?
- Tracer Bullets - style of development that is only way to keep up with pace of modern life.
- Prototypes and Post-it Notes - How to test architectures, algorithms, interfaces, ideas before committing to them?
- Domain Languages - some suggestions which can be implemented.
- Estimating - How to get good at working out how long things will take?

## The Essence of Good Design

- The world is full of gurus and pandits, all eager to pass on their hard-earned wisdom when it comes to "How to Design Software".
- There are a lot of information out their in internet. But, what is good design?

> Good Design is Easier to Change Than Bad Design

 - A thing is well designed if it adapts to the people who use it.
 - For code, that means it must adapt to changing.
 - ETC principle: Easier to Change. Every design principle is an special case of ETC.
    - Decoupling - Because of isolating concerns we make change easy. ETC!
    - Single Responsibility principle - When we need to change, we have to do only in 1 module. ETC!
    - Naming - Easy to understand code. Why? To change. ETC!

### ETC is a Value, Not a Rule

 - Values help you make tough decisions easy. Should I do this or that?
 - In software, ETC is a guide, helping to choose between paths which should be a concious thought, subtly nudging you in the right direction.
 - How do you make this happen?
    - Requires some initial conscious reinforcement.
    - For every file you save, fix a bug, write a test (if you do :) ask,
        - Did the thing I just did make the overall system easier or harder to change?
 - ETC assumes that a person can decide which of the multiple paths would be easier to change in the future based on common sense.
 - If you are not able to choose a path, that's OK. In those cases,
    - First, you would not be aware what kind of change would happen.
    - Fallback to "easy to change" path, trying to write replacable code by having it decoupled and cohesive.
    - Seems extreme, but we are supposed to do this all the time.
    - The code that you write should not become an roadblock for change to happen in future.
    - Second, reach out to your instincts.
    - Take a guess what kind of change would be needed in future and tag it in the code (as a comment)
    - So when the change happens, you can give feedback to yourself and it will help you in future fork in the road.
 - All other topics in this chapter are motivated by this one principle, ETC.

 ### Challenges

  - Think about a design principle you use regularly. Is it intended to make things easy-to-change?
  - Also think about languages and programming paradigms (OO, FP, Reactive, and so on). Do any have either big positives or big negatives when it comes to helping you write ETC code? Do any have both?
    - When coding, what can you do to eliminate the negatives and accentuate the positives?
  - Many editors have support (either built-in or via extensions) to run commands when you save a file. Get your editor to popup an ETC? message every time you save (or 10th time) and use it as a cue to think about the code you just wrote. Is it easy to change?

  ## DRY - The Evils of Duplication

   - Best way to disabling a marauding artificial intelligence - give 2 pieces of contradicting knowledge to a computer.
   - Same principle is effective in bringing down your code.
   - Programmers collect, organize, maintian and harness knowledge.
   - Knowledge is documented in specifications, comes alive in code and used to validate things in testing.
   - Knowledge isn't stable. It changes very frequently after a meeting with client, when regulations change and when we know the approach we have chosen does not work.
   - When it changes, you re-organize and re-express it in some form which is true at that time.
   - Maintenance is not a discrete activity that happens post production with just bug fixes and enhancements but a routine part of development process.
   - Maintenance happens each day long before the application is fully developed and released to the end customer.
   - You maintain knowledge from day 1 of project either knowingly or unknowingly.
   - When we maintain we need to find and change what you have earlier done - code, documentation, API, etc...
   - We invite a maintenance nightmare by doing the easiest thing to do - duplicate knowledge in multiple places.

   ### Solution ?

   - The only way to develop software reliably and to make our developments easier to maintain is to follow the DRY principle.

   > Every piece of knowledge must have a single, unambiguous, authoritative representation within a system.

   > DRY - Don't Repeat Yourself

   - What happens when you do not follow DRY ?
      - You represent the same thing in 2 or more places in different ways (sometimes it even takes time to understand it is the same thing).
      - When you have to change in 1 place you have to remember to change in other places.
      - It is not a question if you will remember, it is a question of when you'll forget.
      - Your software will come to its knees with the wave of changes that happens in outside world with this duplication.

   ### DRY is More Than Code

   - DRY is not just about not copying source code or having same code in multiple places (authors correct from 1st edition).
   - Code duplication is part of DRY but a very tiny part.
   - It is more about not duplicating knowledge or intent.

   ### Duplication in Code

   - Though trivial, it is so common.
   - Let us look at below code.
   ![Original Code](images/Original_code.jpg)
   - What are the instances where DRY is violated?

   1. Copy paste duplication for handling negative numbers - fixing that,
   ![DRY Change 1](images/DRY_change1.jpg)
   2. Repetition of field width specification in each printf call. Fixing that using existing function,
   ![DRY Change 2](images/DRY_change2.jpg)
   3. What if we need an extra space between the field labels and numbers? We need to change in each printf. Fixing that,
   ![DRY Change 3](images/DRY_change3.jpg)

   - Result?
      - Want to change number format - change format_amount function.
      - Want to change label format or spacing - change report_line function.

   ### Not all Code Duplication is Knowledge Duplication

   - Below is an example of an false positive.
   ![DRY False Positive](images/false_positive.jpg)

   - Though the code is same in above definitions, we are validating 2 differetent real world entities that might have different set of things to be done in future.
   - It is just coincidence we are doing same thing with age and quantity at present. It may not stay the same in future.

   ### Duplication in Documentation

   - **Myth**: You should comment all your functions.
   - No. Not required. Identify DRY violation in below snippet.
   ![DRY Documentation](images/DRY_documentation.jpg)

   - Fix:
   ![DRY Documentation fix](images/DRY_documentation_fix.jpg)

   - When code is readable, comments are redundant.
   - Above avoids changing in 2 places, once in code and again in comments and mostly we miss changing comments.

   ### DRY violations in Data

   - Data Structures represent knowledge and that could also violate DRY principle.

   - Snippet of Class with some properties:
   ![DRY Data 1](images/DRY_data1.jpg)

   - At 1st sight, above class look fine.
   - But, can we not derive length from other two properties?
   ![DRY Data 2](images/DRY_data2.jpg)

   - There might be concerns that this might not allow the data to cache and result in poor performance.
   - To mitigate that, keep the impact local by using private modifiers so that the code outside the class does not know that this is calculated each time.
   ![DRY Local Impact](images/DRY_local_impact.jpg)

   - In above example, we are still coupling the code that uses a structure to implementation of the module.
   - Try to use accessor functions wherever possible. This will make future changes easier. ETC!

   - Meyer's Uniform Access Principle
   > All services offered by a module should be available through a uniform notation, which does not betray whether they are implemented through storage or through computation.

   ### Representational Duplication

   - Our code interacts with outside world libraries via APIs, services via remote calls, gets data from external sources and so on.
   - For all the above your code (and the external thing you communicate with) needs to be in sync with the knowledge of how to communicate (schema) and what the error codes mean?
   - This gives a chance for DRY violation as the same knowledge is duplicated in your code and also in the external thing.
   - Changing any one breaks the other.
   - Though this duplication is inevitable, it can be mitigated by following strategies.

   #### Duplication Across Internal APIs

   - Identify tools that will generate documentation automatically from your code (which would be neutral)
   - These tools can be used to create functional tests, API clients in different languages to test your API
   - Creates a shared repository which can be used by external world and once you change anything in your API the tool will get updated automatically

   #### Duplication Across External APIs

   - Use OpenAPI specification to get information about public APIs
   - This provides a language agnostice way (or) a common syntax for APIs in different languages to understand the API and communicate with it
   ![OpenAPI Definition](images/OpenAPI.jpg)
   - If you don't find an OpenAPI specification, create and publish it.

   #### Duplication with Data Sources

   - Create containers to store data from external data source using their schema.
   - Another option is to
      - Instead of representing external data in fixed structure like struct, class using key/value data structure will make flexible.
      - In addition to above do validations that will make sure you are getting the data you expect as key/value data structure stores any data type.

   ### Interdeveloper Duplication

   - Hardest type of duplication to detect
   - Entire sets of functionalities would be duplicated between developers and would go undetected for years
   - In a audit in US, it was found that there were 10,000 programs that contained a different version of Social Security Number validation code.

   ![Shocked emoji](images/shocked-emoji-smiley.png)

   - How to solve this?
      - At a high level, build a strong, tight-knit team with **good communications**
      - At a module level, it is challenging as common functionalities or data does not fall into as a single person responsibility (that is why it is common)
      - Best way to deal with this is again encouraging active and frequent communication between developers in the team.
      - Can be best achieved by knowledge sharing and we can identify common areas and work together to avoid duplicated knowledge.
      - An good example is discourse we have at Axelerant where common problems and solutions are available.
      - Look into other people code when needed if there is commonality and also be open when others' would want to look at your code. We are sharing and improving our knowledge.

   > Make it Easy to Reuse

      - If it isn't easy, people would not do it.
      - If you fail to reuse, you risk duplicating knowledge.

   ## Orthogonality

   - Critical concept to produce systems that are easy to design, build, test and extend.
   - Causes immediate improvements in quality of systems if applied directly.

   ### What is Orthogonality?

   ![Orthogonality](images/Perpendicular-coloured.svg)

   - 2 lines are orthogonal if they meet at right angles (90 degrees)
   - In computing, it denotes independence or decoupling
   - Two or more things are orthogonal, if changes in one does not affect any of the others.
   - E.g. Database logic and User interface
   - Real word example: Helicopter controls are decidedly not orthogonal.

   ### Benefits of Orthogonality

   > Eliminate Effects Between Unrelated Things

   - Nonorthogonal systems are inherently more complex to change and control as changing one thing breaks lot of others.
   - Components to be:
      - self-contained: does not depend on other components to achieve its purpose and hence can function independently by its own.
      - single well defined purpose: single responsibility principle
   - Any change in component does not affect the external system and we need to test only that component.
   - We need to be careful only when we change the external interfaces of the component (how it communicates with other components)

   #### Gain Productivity

   - Localised changes, so development and testing time reduced
   - Easier to write small peices of code that performs a unique functionality and test it rather than writing large lines of code that performs a lot
   - Need more funtionality? Add new component rather than changing existing code
   - Produces loosely coupled systems that are easy to reegineer and reconfigure
   - Allows you to innovate
   - 2 orthogonal components that does M and N unique things when combined produces M*N functionalities rather than 2 nonorthogonal components which has overlaps and hence less functionalities

   #### Reduce Risk

   - If a component/module is sick it is already isolated as per design and we can focus on that alone and replace it
   - Resulting system is less fragile as any changes only affects that component
   - Easy to create and run tests as you need to do that only for 1 component and not for entire system
   - Not tighly tied to third part vendors as intefaces to these components are isolated and can be changed easily

   ### How to apply Orthogonality?
   ### Design
   - Developers use the words modular, component-based and layered to denote the process of creating orthogonal systems (we just don't know these mean orthogonality though we use them).

   #### What is an orthogonal system?
   - One that is composed of a set of cooperating modules/components, each of which implements functionality independent of others.

   #### Layering
   - Independent components organized into layers each providing a level of abstraction.
   - Each layer uses the abstractions provided by above layer and is not aware of what exactly it is doing.
   - This allows us to change implementations without affecting code.
   - Reduces the risk of runaway(out of control, challenging to detect) dependencies between modules.
   - Usually denoted via diagrams as given below.

   ![Layering](images/layering.png)

   #### How do you test if a design is orthogonal?
   - After you mapped out what components you are going to have in your system, ask the following question.

   > If I dramatically change the requirements behind a particular function, how many modules are affected?

   - In an orthogonal system, the answer should be one.
   - Though above is naive and in real world requirements any change will affect more than one module.
   - However if you split up the change in terms of functional requirements then each requirement should ideally affect just 1 module.

   #### Example:
   - System for monitoring and controlling a heating plant.
   - The original requirement to have a Graphical UI was changed to have a mobile UI so that engineers can monitor key values on the move.
   - In an orthogonal system what would you expect to be changed ?
   - Only those modules associated with UI/FE design would need to be changed not the actual logic to calculate the key values.

   - Ask yourself below question.
      - How decoupled your design is from changes in the real world?
      - Are you using telephone number, postal codes, government IDs as customer identifier? What happens when they change?

   > Don't rely on the properties of things you can't control.

   ### Toolkits and Libraries
   - Important to preserve orthgonality of your system as you introduce third party toolkits and libraries.
   - Choose your technologies wisely.
   - When bringing in toolkit (or library) from external world or even internal (other member of your team/organization) ask yourself whether it imposes changes on your code that shouldn't be there.
   - For example, let us say you need to tweak the way you send input to meet the requirements of an external service.
   - What happens if the external service change their input parameters in next release?
   - Better to have such third party dependent code isolated from your actual system so that you can at least identify them easily. Better do the tweak in external service itself (colloborate with author).
   - Author gives example of Enterprise Java Beans (EJB) where transactions start and end are denoted via annotations rather than embedding them into the application code. This allows the same code to be used in different transactions.
   - Above is an example of Decorator pattern: adding functionality to things without changing them.

   ### Coding
   - Every time to write code you run the risk on reducing the orthogonality of your system.
   - You need to constantly monitor the larger context of the system rather than being focussed on the current "what you are doing" aspect.
   - Otherwise there is good chance you will repeat already existing knowledge (DRY) which is birthplace of non-orthogonal systems.

   #### Techniques to maintain orthogonality
   #### Keep your code decoupled
   - Write shy code - modules that don't reveal anything unnecessary to other modules and that don't rely on other modules' implementations.
   - e.g. If you need to change an object's state, get the object to do it for you.

   #### Avoid global data
   - Every time your code references global data, it ties itself into the other components that share that data.
   - Even read only global data can cause trouble. e.g. if you want your application to be multithreaded.
   - Suggested way is to pass any context needed for your module (i.e.) passing parameters to constructors in OOP
   - Be careful when using Singleton objects as global variables (done in Java that do not support globals) as it can also lead to unnecessary linkage.

   #### Avoid similar functions
   - Avoid functions which has similar start and end but different central algorithm.
   - Duplicate code is symptom of structural problems.
   - Author suggests to check [Strategy pattern](https://en.wikipedia.org/wiki/Strategy_pattern).

   ### Testing
   - An orthogonally designed and implemented system is easier to test.
   - Testing can be done more at module/unit level rather than doing an integration testing as each module is independent and if they work then entire system works.
   - Author suggests to automate this testing in build process (CI/CD).
   - Writing unit tests will expose non-orthogonal code as you will know if you need to pull in large percentage of rest of your code (outside of the unit you are testing).
   - Bug fixing also reveals orthogonality as based on the fact that fix given is how local or you need to change a lot of modules/entire system?
   - Also when you fix a bug does it fix the bug or cause other regression?
   - You can automate to run monthly reports to check how each bug fix changes your code and to what extent? You need to tag your repo for each bug fix.

   ### Documentation
   - Yes! Orthogonality also applies to documentation.
   - The axes are content and presentation.
   - Does changing the presentation of your document require changing content?
   - Best example is this... yes this.. Markdown (md) where we focus only on content and presentation is taken care by itself.

   ### Living with Orthogonality
   - Orthgonality is closely related to DRY as we have seen.
      - DRY - Reduce duplication in the system.
      - Orthogonality - Reduce interdependency in the system (which is easy if DRY is followed)
   - When using together they create systems that are more flexible, more understandable, easy to debug, test and maintain.
   - If you are in a project where people try to change things and every change causes 4 other things to break - then its time to refractor a non-orthogonal system.

   ### Challenges
   - Consider the difference between tools which have a graphical user interface and small but combinable command-line utilities used at shell prompts.Which set is more orthogonal, and why? Which is easier to use for exactly the purpose for which it was intended? Which set is easier to combine with other tools to meet new challenges? Which set is easier to learn?
      - Editors like VSCode, PHPStorm, Eclipse

   - C++ supports multiple inheritance, and Java allows a class to implement multiple interfaces. Ruby has mixins. What impact does using these facilities have on orthogonality? Is there a difference in impact between using multiple inheritance and multiple interfaces? Is there a difference between using delegation and using inheritance?

   ### Exercises
   #### Exercise 1

   ![Exercise 1](images/Ortho.png)

   #### Exercise 2
   - What are the differences in orthogonality between object-oriented and functional languages? Are these differences inherent in the languages themselves, or just the way people use them?

   ## Reversibility

   > Nothing is more dangerous than an idea if it's the only one you have.

   - Engineers prefer simple, singular solutions to problems.
   - Management tends to agree with the engineers: singular, easy answers fit nicely on spreadsheets and project plans.
   - If only the real world would cooperate!
   - If you rely heavily on some fact, you can almost guarantee that it will change.
   - There is always more than 1 way to implement anything.
   - More than 1 vendor who can provide a third party product.
   - More than 1 solution to any problem.
   - Unless you accept above, you may be in for an unpleasant surprise.

   > But you said we'd use database XYZ! We are 85% done coding the project, we can't change now!" the programmer protested. "Sorry, but your company decided to standardize on database PDO instead-for all projects. It's out of my hands. We'll just have to recode. All of you will be working weekends until further notice."

   - With every critical decision, the project team commits to a smaller target-a narrower version of reality that has fewer options.
   - By the time many critical decisions have been made, the target becomes so small that if it moves, or the wind changes direction, or a butterfly in Tokyo flaps its wings, you miss. An you may miss by a huge amount.
   - The problem is that critical decision aren't easily reversible.
   - E.g. once you decide to use this vendor's database, or that architectural pattern, or a certain deployment model, you are committed to a course of action that cannot be undone, except at great expense.

   ### So what is reversibility?
   - Author points out that many topics in the book are geared to producing feasible, adaptable software
   - By following the below in this book, we don't have to make as many critical, irreversibe decisions.
      - DRY principle
      - Decoupling
      - use of external configuration
   - Not making irreversible decisions is good as we don't always make the best decisions the first time
   - Requirements, users, hardware change faster than we can get the software developed.
   - Example of making changes that are usually irrevesible:
      - Changing from relational to document database once you find out that the relational is too slow to cater user needs.
      - Starting the project as browser based app but marketing decides it needs to be mobile app.
   - The mistake lies in assuming that any decision is cast in stone-and in not preparing for the contingencies that might arise.
   - Software decisions are not carved in stone but in sand where a big wave can wipe it out anytime.

   > There Are No Final Decisions

   ### Flexible Architecture
   - Below are some "best practice" server-side architectures:
      - Big hunk of iron
      - Federations of big iron
      - Load-balanced clusters of commodity hardware
      - Cloud-based virtual machines running applications
      - Cloud-based virtual machines running services
      - Containerized versions of the above
      - Cloud-supported serverless applications
      - And, inevitably, an apparent move back to big hunks of iron for some tasks

   - It's a miracle that anything ever worked.
   - So how can you plan for this kind of architectural volatality? You can't.

   - But you can make your application easy to change (ETC again):
      - Break code into components even if deployed to single server. This approach is easier than splitting an monolithic application later on.
      - Hide third party API's behind your own abstraction layers
   - No one knows what the future may hold, especially not us !
   - So enable rock-n-roll: to "rock-on" when it can, to roll with the punches when it must.

   ## Tracer Bullets

   > Ready, fire, aim... - Anon

   ### What are they?
   - We talk about hitting targets when we develop software.
   - Though we are not firing anything at the shooting range, it's a useful and very visual metaphor.
   - It's interesting to consider _how_ to hit a target in a complex and shifting world like software development.

   - Whether you hit the target of course depends a lot on the nature of device you aim with.
   - Usually you hit and then see if you have got the target but there is a better way.

   - Author refers to movies, video games and TV shows where when people hit with guns we see a visible path of bullets as bright streaks in the air.
   - These visible streaks in air comes from tracer bullets which are loaded in intervals along with regular ammunition.

   - Why tracer bullets?
      - Real time immediate feedback to soliders to refine their aim
      - Again, a pragmatic approach

   - Same applies to software projects, particularly when you're building something that hasn't been built before.
      - On a side note, sometimes we think we are just putting pieces together in software but note that the way we put them together is unique and hence we end up creating unique systems.
   - We use the term _tracer bullet development_ to visually illustrate the need for immediate feedback under actual conditions with a moving goal.

   - What are the moving goals?
      - Since your users have not seen anything like what you are developing, the requirements may be vague or may change.
      - You maybe using algorithms, techniques, languages, or libraries you aren't familiar with as a result there are many unknowns.
      - Projects take time to complete and hence the environment/platform you are working on may change before you're done.

   - What is the classic response to this?
      - Write out every requirement freeze them
      - Trying to grasp every known unknown and avoiding unknown unknowns as if they are not there.
      - Constraining ourselves to a type of environment
      - One big calculation upfront, then shoot and hope nothing changes.
   - Result?
      - Create a system that dies eventually

   - Pragmatic Programmers, tend to prefer using the software equivalent of tracer bullets.

   ### Code That Glows in the Dark
   - Tracer bullets operate in same environment with same constraints as real bullets.
   - Immediate feedback to the gunner.

   - To get similar effect in code, we look for something that gets us from requirement to some aspect of final system quickly, visibly, and repeatably.

   - How to do this in code?
      - Look for important requirements of the system - the Must Haves to start with
      - Look for the grey areas which has the huge risk of implementation
   - Then, prioritize your development so that these are the first areas you code.

   > Use Tracer Bullets to Find the Target

   - The very first tracer bullet is Hello World
   - Then built the skeleton of the system which is needed

   #### An example
   ![Architectural Layers](images/architectural_layers.jpg)

   - Above system has five architectural layers.
   - To understand how we can integrate them, we do a simple feature that uses all the layers.
   - The diagonal line shows the path that feature takes through the code.
   - To make the feature work, we need to just implement the solidly shaded areas in the diagram and the stuff with the squiggles will be done later.

   Below is an example,
   - Assume a complex client-server database marketing project.
   - Part of the requirement was ability to specify and execute [temporal queries](https://blog.devgenius.io/a-query-in-time-introduction-to-sql-server-temporal-tables-145ddb1355d9).
   - DB servers were a range of relational and specialized databases.
   - Client UI written in random language A, used set of libraries written in different language provide interface to the servers.
   - User's query stored on the server in a Lisp-like notation before being converted to optimized SQL prior to execution.
   - Many unknowns, many environments and no one was too sure how the UI should behave.

   - Above is a great opportunity to use tracer code by,
      - Developed a framework for the front end, libraries representing the queries.
      - Structure for converting a stored query into a DB specific query.
   - Then, it above together and checked that it worked.
   - Wrote a query to fetch rows from table with above structure and it worked.
   - This proves that the UI could talk to libraries, libraries could serialize and de-serialize the queries and the corresponding databases can infact retireve the results for the query.
   - Over few months more types of queries where added and the library was enhanced

   - Tracer code is not disposable rather you keep it in the final system
   - It contains all error checking, structuring, documentation and self-checking that any production code has.
   - Only difference is that it is not fully functional.
   - You achieve an end to end connection among the different components or parts of the system and build on top of that.