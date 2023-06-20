# Regex-Tutorial

The purpose of this Regex tutorial is to provide an explanation of how regular expressions (or regex) can be utilized to validate phone numbers within a specified format.

# Summary

## `/^\(?([0-9]{3})\)?[-. ]?([0-9]{3})[-. ]?([0-9]{4})$/`

In summary, this regular expression can be used to match phone numbers in the following formats:

- `555-123-4567`
- `555.123.4567`
- `555 123 4567`
- `(555)-123-4567`
- `(555).123.4567`
- `(555) 123 4567`

<br>

**Note that the regular expression doesn't validate whether the phone number is actually assigned or valid. It only checks if the provided format matches the pattern.


# Table of Contents

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

# Regex Components
## Anchors
`/^` and `$/` indicate the start and end of the string, respectively. This ensures that the entire string is matched and not just a portion of it.

## Quantifiers
- `?` - The question mark quantifier makes the preceding character or group optional. In this pattern, it is used after the opening and closing parentheses `\(` and `\)` to indicate that they are optional. This allows for phone numbers to be provided with or without parentheses around the area code.

- `{n}` - The curly braces with a number inside indicate a specific repetition count. In this pattern, `{3}` is used after `[0-9]` to match exactly three digits. Similarly, `{4}` is used after `[0-9]` to match exactly four digits.

These quantifiers modify the behavior of the regular expression and allow for flexibility in the matching pattern.

## OR Operator
In this regular expression pattern, the OR operator is not explicitly used. However, there are elements within the pattern that provide options, achieving a similar effect to the OR operator.

The elements that provide options are the square brackets `[ ]` and the hyphen `-`. These elements create a character class, allowing different characters to be matched at a specific position.

For example, `[-. ]?` matches an optional character that can be a hyphen, dot, or space. The hyphen `-` inside the square brackets indicates a range, allowing the pattern to match any of the characters within that range.

By using character classes and ranges, the pattern can match different variations of separators between digits, such as hyphens, dots, or spaces.

## Character Classes
There are two instances of character classes:

- `[0-9]` - This character class matches any digit from `0` to `9`. It is used to match the digits in the phone number. For example, `([0-9]{3})` matches exactly three digits in the area code and `([0-9]{4})` matches exactly four digits in the last part of the phone number.

- `[-. ]` - This character class matches a single character that can be a hyphen, a dot, or a space. It allows for different separators between the digits of the phone number. For example, `[-. ]?` makes the separator character optional, allowing for variations like `"555-123-4567"`, `"555.123.4567"`, or `"555 123 4567"`.

Character classes are enclosed within square brackets `[ ]` and define a set of characters that can match at a particular position in the pattern. By using character classes, the regular expression can be flexible and match different characters within a specified range or set of options.

## Flags
There are no flags used in this expression.

Flags in regular expressions are optional settings that can modify the behavior of the pattern matching process. They are usually specified after the closing delimiter of the regular expression, such as /pattern/flags.

Common flags used in regular expressions include:

- `i (case-insensitive)` - Allows matching to be case-insensitive, ignoring the distinction between uppercase and lowercase letters.

- `g (global)` - Causes the regular expression to search for all occurrences of the pattern throughout the entire input string, rather than stopping after the first match.

- `m (multiline)` - Changes the behavior of the `^` and `$` anchors, making them match the start and end of each line within a multiline input string.
However, in the given regular expression pattern, no flags are present. It is a simple pattern for matching phone numbers in a specific format.

## Grouping and Capturing
This pattern uses parentheses `( )` to define groups that capture specific portions of the matched string. These captured groups can be referenced or extracted later for further processing.

- `([0-9]{3})` - This group captures exactly three digits (0-9), representing the area code of the phone number. It is enclosed within parentheses `( )` to create a capturing group.

- `([0-9]{3})` - This group captures another three digits (0-9), representing the next three digits of the phone number.

- `([0-9]{4})` - This group captures the last four digits of the phone number.

## Bracket Expressions
The bracket expression used in this pattern is `[0-9]`, which matches any single digit from `0` to `9`. It represents a character class that specifies a range of characters that can match at a particular position in the pattern.

`[0-9]` is used multiple times in the pattern to match the digits in the phone number, specifically used in the following parts of the pattern:

- `([0-9]{3})` - This matches exactly three consecutive digits `(0-9)`, representing the area code of the phone number.

- `([0-9]{3})` - This matches another three consecutive digits `(0-9)`, representing the next three digits of the phone number.

- `([0-9]{4})` - This matches exactly four consecutive digits `(0-9)`, representing the last four digits of the phone number.

## Greedy and Lazy Match
There are no explicit greedy or lazy matches used in this expression.

Greedy and lazy quantifiers determine the behavior of the matching process when there are multiple occurrences of a pattern to be matched. However, in this particular pattern, there are no quantifiers that directly control greediness or laziness.

Instead, the pattern uses optional characters and character classes to allow for flexibility in matching different formats of phone numbers. The quantifiers `? (indicating zero or one occurrence)` and `{3} (indicating exactly three occurrences)` specify the exact number of digits to be matched.

## Boundaries
`^` - The caret symbol at the beginning of the pattern represents the start of a line or string. It asserts that the following pattern should match at the beginning of the input.

`$` - The dollar sign at the end of the pattern represents the end of a line or string. It asserts that the preceding pattern should match at the end of the input.

Together, `^` and `$` form the start and end boundaries of the input string. This ensures that the entire input string must match the entire pattern, from start to finish.

By using these boundary anchors, the regular expression enforces that the phone number must match the specified format completely, without any additional characters before or after.

## Back-references
Back-references are used in regular expressions to refer back to a previously matched group within the same pattern. They are typically represented by the backslash followed by a digit `(e.g., \1, \2, etc.)` corresponding to the capturing group's position.

However, in the given pattern, there are capturing groups `( )`, but they are not referenced within the pattern itself. Instead, the capturing groups are used to capture specific portions of the matched phone number, allowing for further processing or extraction if needed.

For example, in a programming language or regular expression engine that supports back-references, you can use the captured groups to reference or extract the area code, three-digit section, and four-digit section of the phone number separately. But within the pattern itself, there are no back-references used.

## Look-ahead and Look-behind
Look-ahead and look-behind assertions are advanced techniques in regular expressions that allow for conditional matching based on patterns that precede or follow the current position in the input string. They are represented by `(?=...)` for look-ahead and `(?<=...)` for look-behind.

In the given pattern, there are no instances of these look-around assertions. The pattern is a straightforward expression for matching phone numbers in a specific format, using capturing groups and character classes to define the structure and allowed characters within the phone number.

Without look-ahead or look-behind assertions, the pattern will match phone numbers that strictly adhere to the provided format, without considering any specific context or conditions before or after the phone number.

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
