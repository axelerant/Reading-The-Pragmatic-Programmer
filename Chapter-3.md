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
