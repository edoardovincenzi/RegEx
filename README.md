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

## Ancors

^ --Starting text or if expression flag ( m ) was able, every starting headed line.

$ --Ending text or if expression flag ( m ) was able, every ending headed line.

\A --If we work with Flag multiline and we want take only the first character about all text we can use this special character

\Z --If we work with Flag multiline and we want take only the last character (exept go ahead space ...) about all text we can use this special character

\z --If we work with Flag multiline and we want take only the last character (include go ahead space ...) about all text we can use this special character

## Special character

. --Every character include spacing, tab ecc


| --Is similar OR math

\\ --Escape character

\* --Zero or illimitate

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

LOOKAROUND
```
(?=???)	Positive lookahead	(?=\d{10})\d{5}	01234 in 0123456789
```
```
(?<=???)	Positive lookbehind	(?<=\d)cat	cat in 1cat
```
```
(?!???)	Negative lookahead	(?!theatre)the\w+	theme
```
````
(?<!???)	Negative lookbehind	\w{3}(?<!mon)ster	Munster
````

IF you want create a group, but not numbered this, you must use "?:" after "(". Es : (?:[a-z])[0-9]

Group into group, in this case the external group have priority for enumbered. External first, internal second.

Regex normally execute code from left to right. If you try to use a reference group ( \2 example ) before group 2 declaration at
first reference \2 will be empty beacause regex execute code from left to right, but if you try to search a more occurence of \2 
( in this example), at secondo and more times \2 will have reference about group 2.

## Escape + character 

(Letters == 0-9 a-z A-Z)

\d --Number 0-9

\h --White spaces orizzontal ( blank, tab )

\s --White spaces ( blank, tab, go ahead )

\w --Any letters

\D --All characters excluding 0-9

\H --All characters excluding white spaces orizzontal ( blank, tab )

\S --All characters excluding white spaces ( blank, tab, go ahead )

\W --All characters exluding letters


## Word boundaries \b

Word boundaries create ancor before and after a letters if these haven't other letters but space or tab ecc

Example:
```
/\bciao/
```

ciao will be match

aciao will not be match


```
/\bciao\b/
```
ciao will be match

ciaoo will not be match

cciao will not be match


## Lazy selection

Normally regex expressions are greedy and try to take the major text if they can.

Example

```
/".*"/g
```

This expression will takes all text from first " until last ".

Hello everybody "It's me". This is a simple text " for summary the principle concept".

In this example the expression will take "It's me ... concept".

If we want take all text inside " ... " we will switch from greedy to lazy capture, using a "?" character.

```
/".*?"/
```

Thanks lazy capture we will take only "It's me", because we said take until first occurence.



