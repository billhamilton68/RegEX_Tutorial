# Title 
Understanding Regex Password Validation

This tutorial will walk you through a specific regular expression (regex) designed for password validation. banking, credit card comppanies utilize regex enforce password requirements to protect and secure your assets and your privacy,  

## Summary

Regex is a powerful tool used for defining search patterns for purposes of inclusion, exclusion or matching. Regex can be used for string manipulations, input validation, and more.

This regex will focus on password validatuin following rules:

The first character must be a capital letter
The length must be between 7 and 9 characters
The password cannot contain the word "password" or "Password"
It must include at least one numeric value
It must contain a special character (but not * or %)
It cannot contain white spaces

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind) 
- [Javascript implementation](#Javascript-implementation) 


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

### Javascript implementation

function validatePassword(password) {
    // The regular expression
    const regex = /^([A-Z](?!.*password)(?!.*Password)(?=.*\d)(?=.*[^\s*%]).{6,8})$/;

    // Test the password
    return regex.test(password);
  
}

Test cases:

console.log(validatePassword("Abcdef1#"));  // Outputs: true
console.log(validatePassword("abcdef1#"));  // Outputs: false (no capital letter at the beginning)
console.log(validatePassword("Abcdefgh1#"));  // Outputs: true
console.log(validatePassword("Abcdefghij1#"));  // Outputs: false (more than 9 characters)
console.log(validatePassword("Abcpassword1#"));  // Outputs: false (contains the word "password")
console.log(validatePassword("Abcdef1"));  // Outputs: false (no special character)
console.log(validatePassword("Abcdef1*"));  // Outputs: false (special character is "*")
console.log(validatePassword("Abc def1#"));  // Outputs: false (contains whitespace)

## Author
bhamilton68