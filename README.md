# RegEx Guide

- [Delimiters](#delimiters)
- [Expression Flags](#expression-flags)
- [Single Character or String](#single-character-or-string)
- [Anchors](#anchors)
- [Special Characters](#special-characters)
- [Lookaround](#lookaround)
- [Escape + Character](#escape--character)
- [Word Boundaries](#word-boundaries)
- [Lazy Selection](#lazy-selection)

  
## Delimiters:
Inside / and /, we will put regex expression.

/  /


## Expression Flags
These expression flags are used to delimit spaces:

- **g**: Global, used to check expressions in the entire text.
- **i**: Insensitive, used to check expressions without considering text case.
- **m**: Multiline
- **s**: Single line (detail)
- **x**: Extended
- **U**: Ungreedy

## Single character or string
You can search for a single character or a string.
When searching for a string, you will explore every single character in the string.
For example, 'was' will match 'char w', 'char a', 'char s'.
Remember that Regex expressions are case-sensitive by default.

`/r/` or `/was/`

## Anchors

- **^**: Starting text or, if the expression flag (m) is enabled, every starting line.
- **$**: Ending text or, if the expression flag (m) is enabled, every ending line.
- **\A**: If we work with the multiline flag and want to take only the first character of the entire text, we can use this special character.
- **\Z**: If we work with the multiline flag and want to take only the last character (excluding trailing spaces) of the entire text, we can use this special character.
- **\z**: If we work with the multiline flag and want to take only the last character (including trailing spaces) of the entire text, we can use this special character.

## Special characters

- **.**: Every character, including spacing, tab, etc.
- **|**: Similar to OR in math.
- **\\**: Escape character.
- **\***: Zero or unlimited occurrences.
- **?**: Zero or one occurrence.
- **!**: Zero or more occurrences.
- **\+**: One or more occurrences.
- **[]**: You can search a range of values with "-" [0-5] or [a-g]. It has the same principle as "|". You can also search a different range [0-4a-b]. Inside [], you mustn't use the escape character, but only for the "^" character. It is usually used to negate the range or character inside [].
- **{}**: Specifies the quantity of elements.

Examples:

- `/a{3}/`: Exactly 3 'a'.
- `/a{2,}/`: 2 or more.
- `/a{1,3}/`: From 1 to 3 times 'a'.

- **()**: Used to create groups. Thanks to these groups, we can apply {} or ? or ! etc., to all content in the group. Each group is numbered from 1 to n, and you can refer to them using the syntax: \n (where n indicates the number of the group).

Note: If you find a string (e.g., "afb") with your group ([a-f]+) and use a reference to this group, the regex will try to search the same string found in the main group and NOT apply the same regex in the group reference.

## LOOKAROUND

- **Positive Lookahead `(?=...)`:**
  - Example: `(?=\d{10})\d{5}` searches for '01234' in '0123456789'.

- **Positive Lookbehind `(?<=...)`:**
  - Example: `(?<=\d)cat` searches for 'cat' in '1cat'.

- **Negative Lookahead `(?!...)`:**
  - Example: `(?!theatre)the\w+` searches for 'theme'.

- **Negative Lookbehind `(?<!...)`:**
  - Example: `\w{3}(?<!mon)ster` searches for 'Munster'.

If you want to create a group that is not numbered, you must use "?:" after "(" (e.g., `(?:[a-z])[0-9]`).

Groups within a group, in this case, the external group has priority for numbering. External first, internal second.

Regex normally executes code from left to right. If you try to use a reference group (\2, for example) before declaring group 2, at first reference, \2 will be empty because the regex executes code from left to right. However, if you try to search for more occurrences of \2 (in this example), at second and subsequent times, \2 will have a reference to group 2.

## Escape + character

(Letters == 0-9 a-z A-Z)

- **\d**: Number 0-9
- **\h**: Horizontal white spaces (blank, tab)
- **\s**: White spaces (blank, tab, go ahead)
- **\w**: Any letters
- **\D**: All characters excluding 0-9
- **\H**: All characters excluding horizontal white spaces (blank, tab)
- **\S**: All characters excluding white spaces (blank, tab, go ahead)
- **\W**: All characters excluding letters

## Word Boundaries

Word boundaries create anchors before and after letters if they don't have other letters but spaces or tabs, etc.

Example:

- `/\bciao/`: 'ciao' will be a match, 'aciao' will not be a match.
- `/\bciao\b/`: 'ciao' will be a match, 'ciaoo' will not be a match, 'cciao' will not be a match.

## Lazy selection

Normally, regex expressions are greedy and try to capture the maximum text possible.

Example:

- `/".*"/g`: This expression captures all text from the first " until the last ".
- `/".*?"/`: Thanks to lazy capture, this expression captures only "It's me" because we specified to capture until the first occurrence.

Feel free to ask if you have any further questions!
