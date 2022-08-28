# RegEx

## Delimiters:
Inside / and / we will put regex expression.

/  /


## Expression Flags
These expression flags is used for delimited space to work 

g --Global, is used for check expression in all text.

i --Insesitive, is used for check expression without considered text sensitive.

m --Multiline

s --Single line (dotall)

x --Extended

U --Ungreedy


## Single character or string
You can search a single character or a string.
You can search a string, but in deep, you will search every single character about your string.
was => char w next, char a next, char s.
Remember that Regex expressions, for default, are case sensitive.

/r/ or /was/


## Special character

. --Every character include spacing, tab ecc

^ --Starting text or if expression flag ( m ) was able, every starting headed line.

$ --Ending text or if expression flag ( m ) was able, every ending headed line.

| --Is similar OR math

\\ --Escape character

? --Zero or one occurrence

! --Zero or more occurrence

\+ --One or more occurrence

[] --You can search a range of value with "-" [0-5] or [a-g] or has the same principle of "|".
Also you can seach a differente range [0-4a-b]. Inside [] you mustn't use escape character, but you must use it only for "^" character.
Normally is used for negate range or character inside [].

{} --How much quantity of element. 

/a{3}/ --Exactly 3 a. 

/a{2,}/ --2 or more. 

/a{1,3}/ --from 1 to 3 times a

() --Is used for create group. Thanks these groups we can apply {} or ? or ! ecc, to all content into group.
Every group are numbered, from 1 to n, and you can refer to these thanks this sintax : \n ( where n indicates number of group.
N.B. If you find, with your group ([a-f]+), a string, for example, "afb" and use reference about this group, regex will try to 
seach the same string found in the main group and NOT apply the same regex in the group reference.

NON CAPTURING

IF you want create a group, but not numbered this, you must use "?:" after "(". Es : (?:[a-z])[0-9]

Group into group, in this case the external group have priority for enumbered. External first, internal second.

Regex normally execute code from left to right. If you try to use a reference group ( \2 example ) before group 2 declaration at
first reference \2 will be empty beacause regex execute code from left to right, but if you try to search a more occurence of \2 
( in this example), at secondo and more times \2 will have reference about group 2.













