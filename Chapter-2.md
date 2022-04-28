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
   TODO



