# Analysis of the components used to match an email using regular expressions/([a-z])/

Regular expressions, shortened as regex, are sequences of characters that define a search pattern in a body of text. One can loosely think of it as using your favorite search engine to search the web. How so? Say I needed more information on suitcases. I would open my preferable search engine, type in suitcase, and it would search the web (body of text) and present links to all websites that are suitcase related. The typing of suitcase in that search engine could be likened to writing and running a regular expression. However, instead of using a literal character, the developer will write a pattern of special characters that tells the program to look for anything that fits the pattern. Using that same illustration, let's now say you searched for travel items. Your search engine will still find links to suitcases, but it may also include passport holders, travel beauty supplies, neck pillows, etc. The search was expanded to fit anything in the travel category versus one specific item you may need to travel. Regex will take a pattern that consists of one or more character literals, operators, or constructs and attempt to match it to any text just like that search engine aforementioned. The syntax is universal in most programming languages and with needed only minor changes if any at all. 


## Summary
So let's look at an example. One common use of regex is finding and/or matching emails. An email looks like 'test123@foo.com'. Let's define the pattern of how an email is written. Emails are written as a set of characters followed by an @ followed by another set of characters followed by a period followed by another set of characters.  So how would I write a regex that could look for this pattern? This tutorial provides clarity on the meaning and structure of matching an email regular expression. Let's use the following snippet of code!

 /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)

## Regex Components

### Anchors
Anchors are found at the beginning and end of each regex and do not stand for a character that needs to be searched but more for positional awareness. The symbols used are '^' to express the beginning of the regex and '&' to express the end. They can be used separately if you are looking only for text that begins or ends with a specific character. However, if you need to check if a pattern matches fully you will need to use both. Notice because we are looking for the pattern of an email, we need more than just the beginning or ending anchors but both! 

### Quantifiers
Quanity is defined as the amount or number of some thing. So if is not by accident that a quantifiers in regex specifies how many characters or groupus of character are needed to fit the pattern. There are many different symbols that can represent a qunatifier, however, the one we have in our snippet of code is '{2,6}'. Do you see it towards the end of the regex? This tells the program to match a string that has between 2 and 6 of the values that proceeds it. In this case that would be any 'a-z' character, '\' , or '.'. If someone used the words 'mangos' or 'mango/' then this part of the the expression would find that term becuase it fits the pattern. However, if the words 'mango!' or 'mangos/' are used they would not fit the pattern due to including a different characters and being longer than 6 characters repsectively.

### OR Operator

### Character Classes
Character classes represent a set of charcters and will tell the regex program to match one out of that character set. Character sets can be defined by backslash \ and a period .. In the middle of our code snippet you will see '\d'. This will tell the regex program to match an single character digit (ie., 7).

### Bracket Expressions

### Greedy and Lazy Match

## Author

I currently work as a chemistry teacher and am learning how to code. From teaching to tech! It is definitely a transition but many soft skills needed in education have been helping me through this process. I’ve noticed that I needed to be a problem solver, patient, creative, and detailed orientated. With multiple years of commanding the attention of teenagers to teach them IUPAC nomenclature when they would rather watch paint dry, I feel I have been able to get pretty good at the aforementioned skills.

SMU's full-stack development boot camp is where I am developing the hard skills to become a full-stack developer. In just a short amount of time I have been exposed to HTML, CSS, and Javascript, Node.js and so much more. Please visit https://github.com/zdSMU22 for my full display of work.