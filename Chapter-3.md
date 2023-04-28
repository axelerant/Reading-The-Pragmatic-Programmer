# The Basic Tools

- Tools amplify your talents.
- Example of woodworker's tools used to explain the importance of tools.
- Tools should be lovingly chosen. Once selected, then comes the learning curve to learn to use them effectively.
- The better your tools, and the better you know how to use them, the more productive you can be.
- Start with a basic set of generally applicable tools, as you gain experience, you will add to this basic set.
- Keep adding to your toolbox regularly (as you gain experience).
- Let need drive your acquisitions, if you come across a situation where you feel your current tools aren't good enough, make a note to look for something different or more powerful that would have helped.
- Many new developers make the mistake of adopting a single power tool (ex. a specific IDE) and never change it. This is a mistake.
- The power of plain text, shell games, power editing.
- Version control system - Why should we use it even for personal things.

## The Power of plain text

- As programmers our base material is knowledge. We gather requirements as knowledge, and then express the knowledge in our designs,
implementations, tests and documents.
- The best format for storing knowledge persistently is plain text.
- Plain text enables us to manipulate knowledge manually and programmatically.
- Data in any other format (apart from plain text), example  encrypted data, the meaning cannot be extracted without the application to parse the data.
- This isn't the case with plain text, we can achieve a self-describing data stream that is independent of application that created it.

### What is plain text?

- Plain text is made up of printable characters in a form that conveys information. ex. a shopping list, student data, patient's information etc..
- Plain text can be simple as shared in the examples above or can be complex as well.
- "bjhbjbjb&*(&*7 ()*()*)()*njkjnkjn" - This is not a plain text because reader may not have any idea on it's significance.

### The power of text

- Plain text doesn't mean that the text is unstructured; HTML, JSON, YAML and so on are all plain text for the following reasons - 
- Insurance against obsolescene
- Leverage existing tools
- Easier testing

#### Insurance against obsolescene

- Human readable forms of data, and self-describing data, will outlive all other forms of data and applications that created them.
- You must know the details of the entire format in order to parse the file successfully.
- Ex. Extracting Social Security number from data like - <SOCIAL-SECURITY_NO>123-098-6754</SOCIAL_SECURITY_NO> is much easier exercise then identifying the SSN code from the data like AC27868368768cjknjk.
- There is a difference between human readable and human understandable.

#### Leverage

- Virtually every tool in computing universe, from Version Control Systems to editor to command-line tools, can operate on plain text.

#### Easier Testing

- Plain text format makes it easier to add, update, or modify the test data without having to create any special tools to do so.


## Shell Games

- From shell prompt, you can invoke your full repertoire of tools, using pipes to combine them in ways never dreamt by their original developers.
- You can perform multiple operations using shell ex. launch applications, debuggers, browsers, editors & utilities, search for files, query status of the system and filter outputs etc..
- By programming the shell, you can build complex macros commands for activities you perform often.
- A question may arise here - Can't you do all these operations equally well by pointing & clicking?
- The simple answer is "no". GUI interfaces can be faster & convenient for simple operations.
- The benefit of GUI is WYSIWYG - What you see is what you get! and the disadvantage is WYSIAYG - What you see is all you get!
- Pragmatic programmers don't just code, or develop object models, or write documentation, or automate the build process -- we do all of these things.
- Gain familiarity with the shell, and you will find your productivity soaring.
- Play around with your command shell, and you will be surprised at how much productive it makes you.

### A shell of your own

- Just as a woodworkker customizes their workspace, a developer should customize their shell. This typically also involves changing the configuration of the terminal program you use.
- Changes like - Setting color theme, configuring a prompt, aliases & shell functions, command completion etc..

## Power Editing

- A developer/engineer should be able to manipulate text as effortlessly as possible, since text is basic raw material of programming.
- In first edition of this book, editor had recommended using a single editor for all tasks such as - coding, documentation, memos, system administration etc..
- In this edition, editor has softened the rule by allowing to use multiple editors but has stressed upon getting fluent in each of them. (Achieve Editor Fluency)
- Will this help save time?
- Yes, according to the example given by editor - Over the course of year, you may gain an additional week if you make your editing just 4% more efficient and you edit for 20 hours a week.
- The real benefit - By becoming fluent, you no longer have to think about the mechanics of editing. (Your thoughts will flow & your programming will benefit)
- Example - Driving a car, someone who is experienced in driving can control the car instinctively.

### What does "Fluent" mean?

Some of the examples of what "Fleuncy" means here - 

- Reindent code following changes.
- Comment & uncomment blocks of code using single command.
- Undo & redo changes.
- Split the editor window into multiple panels and navigate between them.
- When editing text, move and make selections by character, word, line and paragraph.
- When editing code, move by various syntactic units (matching delimeters, functions, modules, ...)
- Navigate to particular line number.
- Sort selected lines.
- Run the current project's tests.
- Display compilation errors in current project.

If your current editor can't do some of these things, maybe it is the time to switch?

### Moving towards fluency

- Take the pragmatic approach to learn the commands - Learn those commands that make your life easier.
- Observe yourself while doing something. If what you are doing is repetitive, get into the habit of thinking "there must be some better way to do it", & then find it.
- One you've find an alternative best way (ex. any shortcut/command), get into the habit of using it again and again by consciously looking for opportunities to use it. After a week or so, you'll find you use it without thinking.

#### Growing your editor

- Editor can be extended by installing some extensions.
- When you find something limited within your editor, search around for an extension that will do your job.
- You can also write your own extension & publish it if the problem that you are facing in your editor is a general one and does not have an existing plugin/extension to solve it.

### Challenges

- No more autorepeat - Turn of autorepeat and instead learn the key sequences to move, select and delete by characters, words, lines & blocks.
- Lose the mouse/trackpad for a week. - Perform operations just by using the keyboard.

## Version Control

_Progress, far from consisting in change, depends on retentiveness._
_Those who cannot remember the past are condemned to repeat it._
_George Santayana, life of Reason_

- Sometimes we look for the operations like - Undo / Redo to go back to previous changes.
- Version control system is a _giant undo key_ - A project wide time machine that can return you to any desired point.
- For some people, this is the limit of the usage of VCS. It is a way to collaborate, deploy pipelines, track issues and do a general team interaction.

### Shared Directories are NOT version control.

#### Teams that share their project source files across a network (internall or using cloud storage).

- While doing this, there's a risk of - losing changes, breaking builds & messing up with each other's work.
- It is like writing concurrent code with shared data and no synchronization mechanism. Use version control.

#### Teams that share their project using both - VCS + files over network (or cloud storage).

- They do this to get the best of both worlds.
- Their sites are accessible anywhere and it's backed up off-site.
- But turns out, this is even worse. There is a risk of losing everything in this case.
- VCS software uses a set of interacting files and directories.
- If two instances simultaneously make changes, the overall state can become corrupted.

### It starts at the source.

- VCS keeps track of every change made in the source code / documentation.
- The power of a VCS is way more than just keeping track of changes -
    -  Who made the changes in a particular line of code?
    -  Difference between current version and last week's.
    -  Lines of code changed in between releases.
    -  Which files get changed more often.
    -  Lets you identify releases for your software.
    -  May keep the files they maintain in a central reprository.
    -  Concurrent editing - Allows making concurrent changes to the same set of files.

- **Always use Version Control System**
   - Even if you are working as a single-person team on a short duration project.
   - Even if it is a thrown away prototype.
   - Even if it is not a source code.
   - Make sure that everything is under version control - documentation, phone number lists, memos to vendors, makfiles, build & release procedures, shell scripts - EVERYTHING.

### Branching Out

- The most powerful and most useful feature is the way VCS lets you isolate islands of developments into branches.
- You can create branches at any point in project's history & any work you do in that branch will be isolated from all other branches.
- Once done with your work on that branch, you can merge it into any other branch in future.
- Branches are like little clone projects.
- Benefit 1 - The isolation these branches provide.
- Benefit 2 - Branches are often at the heart of a team project workflow.

Hence, use VCS in your project and if you bump into workflow issues, search for possible solutions.

### Challenges

- Learn & practice the commands to rollback to any previous state of the project using VCS.
- Use VCS for non project things too.
- Explore the features of your current VCS and hosting provider that you are not using. If your team is not using feature branches, experiment with introducing them.
- Spend some time thinking about recovering your own laptop environment in case of a disaster. What would you need to recover? Most of them would just be text files. If they are not in VCS, then add them.

## Debugging

> _It is a painful thing, to look at your own trouble and know that you yourself and no one else has made it._ - Sophocles, Ajax

- The word `bug` has been used to describe an "object of terror" ever since fourteenth centuri.
- The first computer bug was observed by Rear Admiral Dr. Grace Hopper, the inventor of COBOL. (Literally) - A moth caught in a relay in an early computer system.
- Regrettably, we still have bugs in the system, albeit not the flying kind.
- Software defects manifests themselves in variety of ways - misunderstood requirements to coding errors.
- No one writes perfect software, so it's a given that debugging will take up a major portion of your day.

### Psychology of Debugging

- Debugging is a sensitive, emotional subject for many developers. Instead of attacking it as a puzzle to be solved, you may encounter denial, finger pointing, lame excuses, or just plain apathy.
- _Embrace the fact that debugging is just problem solving, and attack it as such._
- Concenrate on _fixing the problem, not the blame._
- A bug is still your problem, whether it is your fault or someone else's.

### A debugging mindset

> _The easiest person to deceive is one's self._ - Edward Bulwer-Lytton, The Disowned

- Before starting to debug, it is important to adopt the right mindset.
- You need to turn off many of the defenses you use each day to protect your ego, tune out any project pressure you may be under, and get yourself comfortable.
- The first rule of debugging - _Don't panic_
- Take a step back, do not panic and actually think about what could be causing the symptoms that you believe indicate a bug.
- If your first reaction is - "_that's impossible_", you are plainly wrong. Because quite clearly, it can and it has.
- Beware of myopia when debugging - Resist the urge to fix just the symptoms you see, it is more likely that the actual fault may be several steps removed from what you are observing and may involve a number of other related things. try to discover the root cause of the problem.

### Where to start

- Make sure that you are working on code that built cleanly - without arnings. We need to concentrate on the harder problems at hand.
- When trying to solve any problem, you need to gather all the relevant data.
- You first need to be accurate in your observations.
- Accuracy in bug reports is further diminished when they come through a third party - You may actually need to watch the user who reported the bug in action to get a sufficient level of detail.
- You may need to interview the user who reported the bug in order to gather more data than you were initially given.
- Artifical tests, in other words writing test cases to make sure what you've built is continuosly tested.

### Debugging Strategies

- Once you think you know what is going on, it's time to find out what the program thinks is going on.

#### Reproducing Bugs

- Best way to start fixing the bug is make it reproducible.
- But instead of going through long processes of reproducing bugs we want something that can help reproduce a bug in a single step (maybe some kind of a command). Because it is lot harder to fix a bug if you have to go through multiple steps to reproduce the bug.
- Here's the most important rule of debugging - 

> _Failing test before fixing code._

- The act of writing test informs the solution.

#### Coder in a strange land

- It is lot harder to find a bug when faced with 50,000 lines of code. How should we isolate the problem area?
- Look at the problem. Is it a crash? Is it about memory? Where is it coming from? Server Side or cleint Side?

> _Read the Damn error message._

##### Bad Results

What if it's not a crash? What if it's just a bad result?

- Get in there with a debugger and use your failing test to trigger the problem.
- A lot of times, we waste long hours trying to track down a bug only to discover that a particular compilation of code worked fine.
- Sometimes the problem is obvious, example: Actual value is different from expected value.
- Why is this value different?
- Move up & down the call stack to find out the exact area of concern.
- Keep a notepad handy to jot down the flow, the steps taken and the clue that you've come across.

##### Sensitivity to input values

- We have all been in a situation where the code works fine with test data & survives few weeks in production.
- Then it suddenly crashes when fed a particular dataset.
- Sometimes it is easier to start with the data.
- Try to get the dataset on local and see where it crashes.

#### The Binary Chop
