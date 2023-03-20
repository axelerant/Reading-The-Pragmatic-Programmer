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
