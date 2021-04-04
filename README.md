# regex-briefing

# What is  a Regular Expression?

A regular expression is a pattern that is matched against a subject string from left to right. Regular expressions are used to replace text within a string, validating forms, extracting a substring from a string based on a pattern match, and so much more. The term "regular expression" is a mouthful, so you will usually find the term abbreviated to "regex" or "regexp".

## Summary
Today we will be looking at and evaluating the following used to match HEX values.

/^#?([a-f0-9]{6}|[a-f0-9]{3})$/

Below we will breakdown the  details of the individual segments that together are used in this regular expression.
 

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

### Flags

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
