# regex-briefing

# What is  a Regular Expression?

A regular expression is a pattern that is matched against a subject string from left to right. Regular expressions are used to replace text within a string, validating forms, extracting a substring from a string based on a pattern match, and so much more. The term "regular expression" is a mouthful, so you will usually find the term abbreviated to "regex" or "regexp".

## Summary
This will be an examination of the following snippet of regex code that is used to match RGB values.

/^#?([a-f0-9]{6}|[a-f0-9]{3})$/

Below we will breakdown the  details of the individual segments that together are used in this regular expression.
The following will be a breakdown of this code and a detailed description of what the individual segments mean and how they are used to make RGB values.
 

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

### Anchors

Anchor: ^ Code Snippet: /^#

Description:

Anchors by themselves do not match any regular expression. Rather they assert something about the string (e.g., beginning, end) based on expressions/matching pattern next to the anchor.

Example: ^This indicates that the string must begin with This

The ^ is an anchor that indicates that the beginning of the string must match the character #. # is used to distinguish a hexadecimal number from a decimal number. However, as we will see in the next anchor, # is optional.

Anchor: $

Code Snippet: $/

Description: Matches the end of the string. Like the ^ anchor, $ is used to check if a string fully matches a pattern. However, $ asserts the pattern to the end of the string, not the beginning.

Example: end$ indicates that the string must end with end.

In our case end of string must match with the 3- or 6-character pattern identified before the $ anchor. The 3- or 6-character pattern is described in more detail under Quantifiers.


### Quantifiers

Quantifier: ?

Code Snippet: /^#?

Description: ? implies a Boolean value, 0 or 1. Typically, this makes the preceding symbol/character optional.

Example: This could be used to distinguish between British and American spelling in a string e.g., colour vs color -- the regex would colou?r

In our regex, the quantifier ? indicates that the character # preceding the quantifier ? is optional. It's optional for # to appear at the beginning of the expression.

Quantifier: {}

Code Snippet: [a-f0-9]{6} Code Snippet: [a-f0-9]{3}

Description:

Quantifier indicates how many times the preceding pattern matches. Normally, the quantifiers are greedy, causing the regex to match as many occurrences of a particular pattern as possible. However, if ? was appended, the quantifier would become lazy-- causing the regex to match as few occurrences as possible. In our case, the quantifier is greedy.

Example: 2{5} indicates that 2 must be repeated 5 times. Matching string must be 22222.

In our regex, {6} indicates that there are 6 instances of the string in the preceding bracket expression. That implies that this quantifier will allow exactly 6 characters in the string containing characters between a-f and/or integer between 0-9. {3} indicates that there are 3 instances of the string in the preceding bracket expression. That implies that this quantifier will allow exactly 3 characters in the string containing characters between a-f and/or integer between 0-9.


### OR Operator

OR Operator: |

Code Snippet: [a-f0-9]{6}|[a-f0-9]{3}

Description: The | indicator (i.e., OR indicator) is a Boolean that matches either the expression before or after.

Example: 3|5 indicates that either 3 or 5 or both integers are allowed in the string. 353 or 333 or 555 are all acceptable matching patterns.

In our case, that implies match with 3-character string containing lower case a-f and/or integer 0-9 OR a string with 6 characters containing lowercase a-f and/or integer between 0-9. A matching string must have 3 or 6 character with the specified pattern. Anything other than 3 or 6 characters will not match.


### Character Classes

In our regex we have one character class that is repeated twice: [a-f0-9]. A character class matches any character enclosed in brackets. For example: [abc] will match "a" or "b" or "c". [-.] will match "-" or ".".

Inside our character class we have two ranges: a-f and 0-9. This means that it matches any character "a" through "f" (lowercase, it will not match uppercase), and "0" through "9". Other examples: [m-p] matches "m", "n", "o" or "p". [3-5] matches "3", "4" or "5"


### Grouping and Capturing

Grouping and Capturing: ()

Code Snippet: ([a-f0-9]{6}|[a-f0-9]{3})

Description: The () groups the regular expression between them. The grouping treats multiple characters as a single unit. This can proof useful when extracting information using any programming language. This group of data will be exposed in the form of an array. Values can be accessed using an index on the result of the match.

Example: (dog){3} matched dogdogdog. The unit of characters 'dog' would need to repeat 3 times indicated in the quantifier.

In our case, the grouped expression is a bracket expression whose details are provided in the section below. Ultimately the end string anchor $ is applied to this grouping.


### Bracket Expressions

Bracket Expression: []

Code Snippet: [a-f0-9]

Description: Bracket expression is a regex that will match a specific pattern of characters (alphabetic, numeric, special characters, symbols etc..) defined within the brackets. Typically, a hyphen is used to describe a set or range of characters e.g. [a-z]. It is possible to use the ^ metacharacter to negate what is in between the brackets.

Example: [a-d 1-3] indicates that the string must include at least 1 character that is between a and d or 1-3

In our reg ex, the bracket [] expression indicates matching a string that has any lower-case character between a-f or any integer between 0-9


### Greedy and Lazy Match

Code Snippet: [a-f0-9]{6} Code Snippet: [a-f0-9]{3}

Quantifier: {}

Description: Greedy means match the longest possible string. Lazy means match the shortest possible string.

Example: w.+l matches well in well but the lazy w.+?l matches wel

Normal quantifiers are greedy, causing the regex to match as many occurrences of a particular pattern as possible. However, if ? was appended, the quantifier would become lazy-- causing the regex to match as few occurrences as possible. In our case, the quantifier is greedy.


## Author

Brad Spurrell
I am an old tradesman with 30 years experience in the printing industry. About a year ago I moved into the digital department and started working  on a computer for the first time in my career. I had a personal computer at home but that was just for internet and paying bills. I liked what a computer could do so now I am here fumbling along trying to learn and keep up as best I can. This has been the best and most difficult experience of my life and I will not give up until I succeed.
My website (still under construction) is https://bspur11.github.io/brad-port/. As I mentioned it needs some, or a lot of work.
Git Repo: https://github.com/bspur11/regex-briefing.git
Gist: https://gist.github.com/bspur11/69a3799b3a8e507009cf3b59b19ebd18






