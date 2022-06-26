# Analysis of the components used to match an email using regular expressions

Regular expressions, shortened as regex, are sequences of characters that define a search pattern in a body of text. One can loosely think of it as using your favorite search engine to search the web. How so? Say I needed more information on suitcases. I would open my preferable search engine, type in suitcase, and it would search the web (body of text) and present links to all websites that are suitcase related. The typing of suitcase in that search engine could be likened to writing and running a regular expression. However, instead of using a literal character, the developer will write a pattern of special characters that tells the program to look for anything that fits the pattern. Using that same illustration, let's now say you searched for travel items. Your search engine will still find links to suitcases, but it may also include passport holders, travel beauty supplies, neck pillows, etc. The search was expanded to fit anything in the travel category versus one specific item you may need to travel. Regex will take a pattern that consists of one or more character literals, operators, or constructs and attempt to match it to any text just like that search engine aforementioned. The syntax is universal in most programming languages and with needed only minor changes if any at all. 


## Summary
So let's look at an example. One common use of regex is finding and/or matching emails. An email looks like 'test123@foo.com'. Let's define the pattern of how an email is written. Emails are written as a set of characters followed by an @ followed by another set of characters followed by a period followed by another set of characters.  So how would I write a regex that could look for this pattern? This tutorial provides clarity on the meaning and structure of matching an email's regular expression. Let's use the following snippet of code!

 /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)


## Regex Components

### Anchors
Anchors are found at the beginning and end of each regex and do not stand for a character that needs to be searched but more for positional awareness. The symbols used are '^' to express the beginning of the regex and '&' to express the end. They can be used separately if you are looking only for text that begins or ends with a specific character. However, if you need to check if a pattern matches fully you will need to use both. Notice because we are looking for the pattern of an email, we need more than just the beginning or ending anchors but both! 

### Quantifiers
Quantity is defined as the amount or number of something. So it is not by accident that a quantifier in regex specifies how many characters or groups of characters are needed to fit the pattern. There are many different symbols that can represent a quantifier, however, the one we have in our snippet of code is '{2,6}'. Do you see it towards the end of the regex? This tells the program to match a string that has between 2 and 6 of the values that precede it. In this case that would be any 'a-z' character, '\', or '.'. If someone used the words 'mangos' or 'mango/' then this part of the expression would find that term because it fits the pattern. However, if the words 'mango!' or 'mangos/' are used they would not fit the pattern due to including different characters and being longer than 6 characters respectively.

### Character Classes
Character classes represent a class, or set, of characters. It will tell the regex program to match one out of that character set. Character sets can be defined by backslash '\' followed by a letter to specify a set or a period '.', which can stand for any character. There are classes for numbers only, alphanumeric and white space characters. In the middle of our code snippet, you will see '\d'. This is a digit character class. This will tell the regex program to match a single character digit (ie., 7).

### Grouping and Capturing
Groupings are denoted with parentheses. Just as if you are working in a group on a project on one final product, this group must also represent one entity. What does that mean? A group of letters could be 'amnwujne' they exist as one functional unit. It can not be 'a' 'm' 'n', etc. because now they are individuals and thus their own separate groups. 

Each parenthesis will apply the regex to the entire grouped text. In other sections, we will break down what these groups mean but first, let's identify how many we have. Remember our code snippet,  /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/? How many groupings do you see?
* 1. ([a-z0-9_\.-]+)
* 2. ([\da-z\.-]+)
* 3. ([a-z\.]{2,6})
There is three total and in each group, there are different components that will define what that group should include. But did you notice some dangling characters? '@' and '\.' aren't part of anyone's groups. That is because they will stand alone and stand for the characters "@" and ".". I will elaborate on why “/.” equals “.” in the next paragraph but for now, let's focus on how this makes sense. We know the structure of an email address is something "@" and email service provider "." a domain so having those characters in between the three parts of the email we can already see how the pattern for the search is taking shape.

### Bracket Expressions
Bracket expressions are used to represent a set of multiple characters. They utilize brackets to open and close the expression hence their namesake. It can consist of one or more expressions that can include characters such as letters, symbols, numbers, and ranges. In our code snippet there are 3 bracket expressions, '[a-z0-9_\.-]', '[\da-z\.-]', and '[a-z\.]'. Whereas they all will follow the same pattern, let's dissect each one. 

The first is [a-z0-9_\.-]. Notice the opening and closing brackets that help clearly denote this as a bracket expression. Inside those brackets, the first this we see is 'a-z'. This denoted a range of any letter a-z. Then we see 0-9. Similar to the a-z expression this is also a range but of numbers 0-9. Lastly, we see characters that are not in a range. Which character do you think it represents? If you said '_', '\', '.', and '-' you would be on the right track but not 100% correct. CONFRIZZLED? The '\' is what is called an escape character. In the [character classes](#character-classes) section, it was mentioned that a '.' can stand for any character. In this instance preceding the '.' with a '\' helps return the character to its original meaning of just representing a '.' and not ANY character. So the first expression is telling us to look for any item that has a combination of one or more of the following:
* letter(s) a-z (of any quantity)
* number(s) 0-9 (of any quantity)
* and/or underscore(s), period(s), and/or hyphen(s) (of any quantity)

Does that make the second bracket expressions a little easier to read? Let's try it! There is one component that is included that we learned about earlier. Do you see it? Yes! Character classes. [\da-z\.-] includes '\d' character classes that means any single digit. Let's draw on what we learned in the last paragraph to decipher bracket expressions. The regex program will look for any item that has one or more of the following:
* a single digit
* letter(s) a-z
* and/or a period or hyphen.
Yes, we still have the escaped character in play on this one!

What is the third expression looking for? If you said any character a-z and/or a '.' you would be right. Great job! Remember, the item will not have to match all the rules only one is needed to be found. Hence why having a regex that is specific to the pattern you are looking for will be very vital.

## Author

Hello, I'm Z'Kiah! I currently work as a chemistry teacher and am learning how to code. From teaching to tech! It is definitely a transition but many soft skills needed in education have been helping me through this process. I’ve noticed that I needed to be a problem solver, patient, creative, and detailed orientated. With multiple years of commanding the attention of teenagers to teach them IUPAC nomenclature when they would rather watch paint dry, I feel I have been able to get pretty good at the aforementioned skills.

SMU's full-stack development boot camp is where I am developing the hard skills to become a full-stack developer. In just a short amount of time I have been exposed to HTML, CSS, and Javascript, Node.js and so much more. Please visit https://github.com/zdSMU22 for my full display of work.