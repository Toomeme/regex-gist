# RegEx Gist - A brief overview of writing regular expressions.
In this gist, we will be breaking down the major components of a regular expression, or Regex. By breaking it down into pieces, you will be equipped with the tools necessary to formulate a regular expression of your own. In addition to this gist, there are many resources for pre-written regex's that can serve not only your project's needs but also as reference material. 

## Summary

A regex is a string that allows you to create search patterns that match given text. For example, a regex for matching an e-mail address would be written as follows:

`/[\w._%+-]+@[\w.-]+\.[a-zA-z]{2,4}/`

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

`/^`#?([0-9a-f]{6}|[0-9a-f]{3})`$/`

The components outlined in the highlighted portion of our regular expression are called anchors. Anchors are used to mark the beginning and end of a string or expression. In this case, `/^` and `$/` denote the beginning and end of our expression, respectively.

### Quantifiers

Quantifiers are used to communicate the expected number of characters. Quantifiers specify the number of instances of a character, group, or character class that must exist in the input for a match to be found. Quantifiers are greedy by default, therefore, will match as many characters as possible. When the characters `"*,+,?,"*` appear in regular expressions, they are quantifiers. The `?` indicates whether the expression should match 0 or 1 time. Because there are two types of formats, we'll use the `or` operator to distinguish which one we're using. We have `{6}` (Hex Triplet Format) and `{3}` (Shorthand Hex Format) in our Hex Value regular expression, which indicates that the length of the component be 6 for `{6}` and 3 for `{3}`.

Example Shorthand Hex Format:
#000, #FFF, #09C
(the Hex Triplet format would double each character: #09C -> #0099CC)

### OR Operator

The `|` element defines the "or" operator within a regular expression. The or operator signifies that it could be either of the components separated by the `|`. Say we have `([0-9a-f]{6}'|'[0-9a-f]{3})` for our hex value regular expression. Take note of the or operator that separates these two components. This means our hex value can be either six characters `[0-9a-f]{6}` or three characters `[0-9a-f]{3}`.

### Character Classes

Character classes are regular expression components that narrow down what characters can appear in the output. Character classes are enclosed in square brackets `[]`. In this example, we have two instances of the same character class: `[a-f0-9]` Within this character class, we can break down what characters are being searched for. 'a-f' looks for letters *a-f* and '0-9' looks for digits *0-9*.

### Flags

Flags change how the expression is interpreted. The flags for JavaScript RegEx's are the following:

`i` - Makes the expression search case-insensitively.

`g` - Makes the expression search for all occurences.

`s` - Makes the wild character `.` match new lines as well.

`m` - Makes the boundary characters `^` and `$` match the beginning and ending of every single line instead of the beginning and ending of the whole string.

`y` - Makes the expression start its searching from the index indicated in its `lastIndex` property.

`u` - Makes the expression assume individual characters as code points, not code units, and therefore, match 32-bit characters as well.

 Flags follow the closing forward slash of the expression. For example: `/.+/igm`.

### Grouping and Capturing

Groups allow you to combine a sequence of tokens to operate on them together. Capture groups can be referenced by a backreference and accessed separately in the results. A capturing group is indicated by parentheses, `()` and groups multiple tokens together for extracting a substring. You can name this capture group to be referenced later using angle brackets.`<>` For example:`(?<laugh>ha)` Additionally, numeric references `/1` match the results of a capture group. For example \1 matches the results of the first capture group & \3 matches the third. By using a colon, `:` you can group matching tokens together without using a capture group. For example:`(?:abc)`

### Bracket Expressions

Bracket expressions in regular expressions signify the beginning of a character class or quantifier statement.

### Greedy and Lazy Match

A greedy match tries to match an element as many times as possible. Whereas, a lazy match tries to match an element as few times as possible. Greedy matching is the default behavior. To enable lazy matching, you would add the `?` quantifier to your expression. 

### Boundaries

A boundary, as the name implies, separates adjascent characters from one another. There are two types of boundaries, `word` and `non-word` (`/b` and `/B`, respectively). A word boundary is a position between a word character and non-word character, or at the beginning or end of a string if it either begins or ends with a word character. A non-word boundary is the negated version of a word boundary, therefore it can only return a match between two word characters, between two non-word characters, between a non-word character and the start or end of the string, and an empty string. As an example, in the string 'Hello World!' a word boundary (`/b`) will match in the following places:

&nbsp;H&nbsp;e&nbsp;l&nbsp;l&nbsp;o&nbsp;&nbsp;,&nbsp;&nbsp;&nbsp;&nbsp;w&nbsp;o&nbsp;r&nbsp;l&nbsp;d&nbsp;&nbsp;!  
^&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;^&nbsp;&nbsp;&nbsp;^&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;^ 

(A non-word boundary (`/B`) will match in the opposite places.)

### Back-references

Captured groups are stored in memory, and can be referenced later. Backreferencing is calling these stored groups to be matched. You can call backreferenced strings using either the capture group's number, or by it's name. 

`/(['"])(.*?)\1/g;` - Calling by number.

`/(?<quote>['"])(.*?)\k<quote>/g` - Calling by name.

### Look-ahead and Look-behind

Look-ahead and Look-behind (lookaround) are `start and end` zero-length assertions, like anchors, but only match characters, then end the match, returning only the boolean: `match` (true) or `no match` (false). They do not consume characters in the string, but only assert whether a match is possible or not. 

Look-ahead syntax:  
Positive: `(?=Y)X`, matches `X`, but only if there’s `Y` after it.  
Negative: `(?!Y)X`, matches `X`, but only if there’s no `Y` after it.  

Look-behind syntax:  
Positive: `(?<=Y)X`, matches `X`, but only if there’s `Y` before it.  
Negative: `(?<!Y)X`, matches `X`, but only if there’s no `Y` before it.

## Author

Jake Toomey is a junior developer enrolled in UCONN's web development bootcamp, and can be found here:

[GitHub Profile](https://github.com/Toomeme)
