# 

# Title Understanding Regex Password Validation

This tutorial will walk you through a specific regular expression (regex) designed for password validation. With this regex, we'll be enforcing security and protecting consumer privacy. 

## Summary

Before we proceed, remember that regex is a powerful tool for defining search patterns, which can be used for string manipulations, input validation, and more.

This regex will focus on the following rules:

The first character must be a capital letter
The length must be between 7 and 9 characters
The password cannot contain the word "password" or "Password"
It must include at least one numeric value
It must contain a special character (but not * or %)
It cannot contain white spaces

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
Anchors are used to specify the position of the pattern in the string. ^ is used to indicate the start and $ for the end of the string.

    Example: ^[A-Z]

The ^ anchor ensures that the first character is a capital letter.

    
### Quantifiers
Quantifiers specify the quantity of characters. {7,9} means between 7 and 9 characters.

Example: ^.{7,9}$

The {7,9} quantifier ensures that the password length is between 7 to 9 characters.

### Character Classes
Character classes specify a group of characters. \d means any digit, and [^\s*%] means any character that's not a white space, * or %.

Example: (?=.*\d)(?=.*[^\s*%])

These lookaheads with character classes inside ensure the password contains at least one digit and one special character that is not a white space, * or %.

### Grouping and Capturing
Parentheses () are used for grouping and capturing. Groups allow us to apply quantifiers to entire patterns, and capturing groups store the matched value.

Example: ^([A-Z](?!.*password)(?!.*Password)(?=.*\d)(?=.*[^\s*%]).{7,9})$

This entire regex ensures that all password rules are met.

The final password validation regex will look like this: ^([A-Z](?!.*password)(?!.*Password)(?=.*\d)(?=.*[^\s*%]).{7,9})$

### Look-ahead and Look-behind
Lookaheads are used to assert a certain pattern is ahead. Negative lookaheads assert that certain patterns are not ahead.

Example: (?!.*password)(?!.*Password)

The (?!.*password) and (?!.*Password) lookaheads ensure that the word "password" or "Password" are not included in the password.
## Author
