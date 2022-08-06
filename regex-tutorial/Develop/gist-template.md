# Your Guide to Regular Expressions: Regex Explored

You may have heard of regular expressions in the past, or even seen them in action. While they may appear daunting just to look at, once you understand the rules of regular expressions, it's really something anyone can easily learn and use! 

Regular expressions, commonly known as Regex, are strings of characters that allow one to specify the search pattern for the string. Using regular expressions efficiently and correctly will allow you to make functional search pattern functionality for users. For example, with Regex one is able to match URL parameters, or create a search and replace feature in a word processor. 

Most programming languages support Regex capabilities, including JavaScript, Java, C, C++, and Python, just to name a few common ones. 

## Summary

Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.

In this tutorial I will be describing how to understand and use regular expressions. There are different components of Regex such as anchors, quantifiers, OR operators, and more (see full Table of Contents below) that will be explained here. You can click any of the titles below to skip to a specific section that you are interested in. 

I will also be explaining the following specific example of a regex email match: 

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

You can observe in the specific regular expression 

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

several regex components. 

### Anchors

Anchors have a unique meaning in Regex and do not match any character. The two anchors are the caret ^ and the dollar sign $. These are very useful and important when validating user input. While they are not a character, anchors instead act as an indicator of position in the string. For example, the ^ caret is used to indicate the position in front of the string. Likewise, $ would match the position after the last character in the string. 

For example, the following code would return true:

let str = "Ezra"
console.log(/^E.test(str));

This would return a value of true because as indicated by the caret ^, E is in the position at the front of the string. 

And this code below would return the value false:

let str = "Ezra"
console.log(/t$/.test(str));

This would return a value of false because as indicated by the $, the test is expecting a 't' in the position at the end of the string, but instead there is the letter 'a'. 

In our specific example, 

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

We can see the caret ^ anchor here indicating that in order for a match to be found, the email must start with a lowercase letter. 

### Quantifiers

Quantifiers are used to indicate how many instances of a character, group, or character class are expected from the input, in order for a match to be identified. Quantifiers attach to one character, character class, or capturing group at a time. For more information on capturing groups, please see the section Grouping and Capturing. 

Quantifiers can be classified into two groups: greedy and lazy quantifiers. Greedy quantifiers cause the regular expression to match as many instances of the particular specified pattern as possible. You can make a quantifier lazy by placing a ? at the end of it. A lazy quantifier causes the regular expression to match as few instances of the specified pattern as possible. For more information on lazy and greedy behavior, please see the Greedy and Lazy Match section. 

The quantifier * is used when you expect a match zero or more times. *? is the lazy version of this quantifier.

The quantifier + is used when you expect a match one or more times. +? is the lazy version of this quantifier. 

The quantifier ? is used to match zero or one time. ?? is the lazy version of this quantifier. 

The quantifier {n} is used to match exactly n times. {n}? is the lazy version of this quantifier. 

The quantifier {n,} is used to match at least n times. {n,}? is the lazy version of this quantifier. 

The quantifier {n,m} is used to match n to m times. {n, m}? is the lazy version of this quantifier. 

For example, 

{n} where n is an integer >= 1 will repeat the previous item exactly n times.	

So, the regular expression e{3} matches eee

In our specific example 

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

We can see the greedy quantifier + two times in this regular expression. First it indicates that in order for the email to match it must have one or more of the following: lowercase letters, digits from zero to nine, and space holders here specified as an underscore, slash, dot, or hyphen. The second quantifier + indicates that the email will need one or more digits, lowercase letter(s), and a space holder like a slash, dot, or hyphen after the @ symbol. 

### OR Operator

The symbol | represents an OR character in the context of regular expressions. For example, 123|789 will match for either 123 OR for 789. 

Our specific example does not contain an OR operator. 

### Character Classes

With character classes, also known as character sets, you can direct the regular expression to match only specified characters. To do this, all you need to do is place the characters you want to match between square  brackets, []. 

For a practical example, if you want to match an a or an e, create the regular expression:

[ae]

This would match both the examples grey and gray, a common difference between American and British English, which is a useful way to utilize character classes in regular expressions. 

In our specific example

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

We can see that there are three character classes, so the regular expression will only match the characters that are inside the brackets. 

### Flags

There are six flags in JavaScript that can affect the search of regular expressions. 

i - with this flag the search is not case sensitive and there would be no difference between A and a. 

g - with this flag, the search looks for all matches. Without it, only the first match is returned. 

m - this flag indicated multiline mode

s - this flag enables dotall which means a dot . can match newline character \n

u - this flag enables full support for Unicode. It activates surrogate pair processing.

y - this flag enables sticky mode, which searches at a precise position within the text. You can perform the search at any given position in the input string. 

Our specific example does not contain any flags. 

### Grouping and Capturing

We already have learned that quantifiers attach to one character, character class, or capturing group at a time. A capturing group is a method for treating multiple charactrers as a single unit together. Capturing groups are created by putting the characters that are being grouped inside of a patenthetical (). 

For example, the regular expression (Ezra) creates a individual group that contains the characters "E", "z", "r", and "a". If a part of the input string matches the capturing group, it will be saved in memory for later recall via backreferences. For more information on this, please see the section Back-references below. 

Our specific example does not group characters, character classes, or capturing groups. 

### Bracket Expressions

A bracket expression in the context of regular expressions comes in between a set of brackets [], and its purpose is to enclose a list of characters that will then match to single characrers in a list, or a range of characters in a list. If the first character in the bracketed list is the caret ^, then it will match characters that are not present in the bracketed list. 

For example, [123] would match 1, 2, or 3.

[a-z] would indicate a match for any letter lowercase a to z in the alphabet. 

[^Ezra] would indicate a match for letters EXCEPT E, z, r, or a. 

Returning to our specific example, 

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

We can see that indeed a caret ^ is used first to indicate that the first characterof our email must be a lowercase letter. The bracketed expressions here are enclosing the different portions of the email that come before and after the @ symbol as well as before and after the dot . symbol.

### Greedy and Lazy Match

In the context of regular expressions, we have two classifications: greedy and lazy. Greedy matching means that the longest possible string will be matched. Lazy means that the shortest possible string will be matched. 

For example, if you had the following string:

abddefghijklmnopqrstuvwxyzc

and you used this expression:

a.*c

This greedy match will match the whole string, because it is recognizing there is a c at the end of the string. However, the following lazy match:

a.*?c 

This, on the other hand, will match only abc because once it processes the first c, the requirements of the regular expression have been satisfied. 

Greedy and lazy matches are not constructed in our specific example. 

### Boundaries

Boundaries, also known as word boundaries, are indicated in regular expressions by \b and they allow you to match for the whole word. 

For example, if we entered the string "Hello, Ezra!" with the regular expression /\bEzra\b/ and entered the following code:

console.log('Hello, Ezra!'.match(/\bEzra\b/));

The output would be "Ezra" because there is an identical match.

It is also possible to use boundaries with digits, for example:

let str = 'I eat dinner at 18:30 PM';
let re = /\b\d\d:\d\d\b/;
let result = str.match(re);

console.log(result);

This will have an output of 18:30 because the example is using the word boundary to find the format hh:mm in the string. 

Boundaries are not utilized in our specific example. 

### Back-references

Back-references are able to match the same text that was matched by a capturing group. This is useful for two main reasons. It allows one to reuse previous patterns and also ensures that two pieces of a string match. You can back-reference in pattern using \N and \k<name>

\N is used to back-reference by number. A group can be identified in the pattern using \N where N is equal to the group number. 

For example, consider we need to find strings that have used quotes, but we need to find either 'Ezra' or "Ezra". We need to identify both of these variants, but we also need to be mindful that we don't want our regular expression to be maching with mixed cases such as "Ezra' or 'Ezra". 

In this case, we would need the following regular expression: 

let regexp = /(['"])(.*?)\1/g;

This works because the regex engine matches with the first quote and memorizes its content, and then further in the pattern the \1 indicates that the regex engine must find the same text that as the first group, which in our scenario would match the same quote, single or double, as the first case. Similarly, \2 would match the second group, and so on. 

/k<name> is used when a regular expression is written using many parentheticals. This allows you to give them names, which can then be referenced again and again. 

In the following example, a group with quotes is named ?<quotation> and thus the back-reference would be \k<quotation>:

let regexp = /(?<quotation>['"])(.*?)\k<quotation>/g;

Back-referencing is not used in our specific example. 

### Look-ahead and Look-behind

Collectively referred to as "lookaround", look-ahead and look-behind are zero-length assertions similar to the start and end of line or start and end of word anchors. The primary difference is that lookaround actually matches characters, but only returns the results: match OR no match. 

In look-ahead, you can use any regular expression EXCEPT a look-behind (more on that in a moment). Capturing groups and back-references in the regular expression will operate as normal. It is important to note that the look-ahead itself is NOT a capturing group. 

There are two types of look-ahead and look-behind: negative and positive. 

Negative look-ahead allows you to match something not followed by another thing. One example is that you can use negative look-ahead to match a q that does not have a u following it. Thus, the u would not be part of the match in a regular expression such as the following: 

q(?!u)

Positive look-ahead, on the other hand, would be able to match a q that DOES have a u following it, as seen in this regular expression:

q(?=u)

Look-behind renders the same effect, but works backwards. A look-behind will indicate to the regex engine to step back in a string and check if the string can be matched there. 

Positive look-behind is written as follows:

(?<=string)

Negative look-behind is written as follows: 

(?<!text)

Negative look-behind would for example, match only a f that is NOT preceded by an e in this regular expression: 

(?<!e)f

It would not match chef, but it would match the f in fed or foot. 

Lookaround is not included in our specific example. 

## Author

Ezra is a former educator with a degree in Liberal Arts from New College of Florida. She a passion for meditation, dance, and making peoples' lives easier using code. Her GitHub is: https://github.com/ezravkatz 