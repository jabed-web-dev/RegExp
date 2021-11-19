# Welcome to RegExp 

### Table of contents
<details><summary>RegExp</summary><blockquote>

  * [`Introduction`](#introduction)
  * [`Match String`](#match-string)
</blockquote></details>

<details><summary>RegExp Methods & Propertys</summary><blockquote>
 
  * [`test()`](#test)
  * [`exec()`](#exec)
  * [`lastIndex`](#lastIndex)
  * [`source`](#source)
  * [`flags`](#flags)
  * [`global`](#global)
  * [`ignoreCase`](#ignoreCase)
  * [`multiline`](#multiline)
  * [`hasIndices`](#hasIndices)
  * [`dotAll`](#dotAll)
  * [`sticky`](#sticky)
  * [`unicode`](#unicode)
</blockquote></details>
 
 
<details><summary>String Methods using RegExp</summary><blockquote>
  
  * [`match()`](#match)
  * [`matchAll()`](#matchAll)
  * [`replace()`](#replace)
  * [`replaceAll()`](#replaceAll)
  * [`search()`](#search)
  * [`split()`](#split)
</blockquote></details>


<details><summary>Flags</summary><blockquote>
  
  * [`g`](#g)
  * [`i`](#i)
  * [`m`](#m)
  * [`d`](#d)
  * [`s`](#s)
  * [`y`](#y)
  * [`u`](#u)
</blockquote></details>


<details><summary>Character classes</summary><blockquote>
  
  * [`•`](#-)
  * [`\w`](#w)
  * [`\W`](#W-1)
  * [`\d`](#d-1)
  * [`\D`](#D-2)
  * [`\s`](#s-1)
  * [`\S`](#S-2)
  * [`\0`](#0)
  * [`\n`](#n)
  * [`\f`](#f)
  * [`\r`](#r)
  * [`\t`](#t)
  * [`\v`](#v)
 </blockquote></details>
 

<details><summary>Unicode Character classes</summary><blockquote>
  
  * [`\xxx`](#xxx)
  * [`\xdd`](#xdd)
  * [`\uhhhh`](#uhhhh)
  * [`\u{hhhhh}`](#uhhhhh)
 </blockquote></details>
 
 
<details><summary>Alternation</summary><blockquote>
  
  * [`^x`](#x)
  * [`x&`](#x-1)
  * [`\bx or x\b`](#bx-or-xb)
  * [`\Bx or x\B`](#bx-or-xb-1)
  * [`x(?=y)`](#xy)
  * [`x(?!y)`](#xy-1)
  * [`(?<=y)x`](#yx)
  * [`(?<!y)x`](#yx-1)
</blockquote></details>

 
<details><summary>Quantifiers</summary><blockquote>
  
  * [`x+`](#x-2)
  * [`x*`](#x-3)
  * [`x?`](#x-4)
  * [`x|y`](#xy-2)
  * [`x{n}`](#xn)
  * [`x{n,}`](#xn-1)
  * [`x{n,m}`](#xnm)
 </blockquote></details>
 
<details><summary>Greedy and Lazy Quantifiers</summary><blockquote>
 
  * [`.+`](#greedy-definition)
  * [`x+?`](#lazy-definition)
  * [`x*?`](#x-6)
  * [`x??`](#x-7)
 </blockquote></details>
 
 
<details><summary>Characters Sets & Ranges</summary><blockquote>
  
  * [`[xyz]`](#xyz)
  * [`[a-z] or [A-Z]`](#a-z-or-a-z)
  * [`[0-9]`](#0-9)
  * [`[^xyz]`](#xyz-1)
  * [`[^a-z]`](#a-z)
  * [`\u{1F600}-\u{1F64F}`](#u1f600-u1f64f)
 </blockquote></details>

 
<details><summary>Groups & ranges</summary><blockquote>
  
  * [`(x)`](#x-8)
  * [`(?:x)`](#x-9)
  * [`(x|y)`](#xy-3)
  * [`(?<name>x)`](#namex)
  * [`\k<name>`](#kname)
  * [`\N`](#n-1)
 </blockquote></details>
 

<details><summary>Unicode property escapes</summary><blockquote>
  
  * [`\p{UnicodeProperty}`](#punicodeProperty)
  * [`\P{UnicodeProperty}`](#punicodeProperty-1)
 </blockquote></details>
 
 
<details><summary>Escaped Characters</summary><blockquote>
  
  * [`\`](#-1)
 </blockquote></details>
 
 
<details><summary>Substitution</summary><blockquote>
  
  * [`$$`](#-2)
  * [`$&`](#-3)
  * [``$` ``](#-4)
  * [`$'`](#-5)
  * [`$n`](#n-2)
  * [`$<name>`](#name)
 </blockquote></details>
 
 
<details><summary>Using variable</summary><blockquote>
  
  * [`regex in variable`](#regex-in-variable)
  * [`replace with function`](#replace-with-function)
</blockquote></details>

_________________________________________________
 
 
 
 
## [RegExp](#Table-of-contents)

### Introduction

> A regular expression is an object that describes a pattern of characters. \
> Regular expressions are used to perform pattern-matching and 'search-and-replace' functions on String

- **Syntax**
```js
// literal
/pattern/modifiers;

// constructor
new RegExp(pattern, modifiers);

```
> Do a `g` for global search for word+o+word in a string match 'row', 'fox' or 'dog'
 
- **Example for literal**
```js
let str = 'The quick brown fox jumps over the lazy dog. It barked.'
let regex = /\wo\w/g;
let matchValue = str.match(regex);
  
console.log(matchValue);
// Output: ['row', 'fox', 'dog']
```
 
- **Example for constructor**
```js
let str = 'The quick brown fox jumps over the lazy dog. It barked.'
let regex = new RegExp(/\wo\w/, 'g');
let matchValue = str.match(regex);
  
console.log(matchValue);
// Output: ['row', 'fox', 'dog']
```
 

### Match String
> **Definition and Usage:**\
> Using a regular expression literal, which consists of a pattern enclosed between slashes.
 
```js
let str = 'fooexample foobar';
let regex = /foo/g;
 
console.log(str.match(regex)) // [ 'foo', 'foo' ]
```
 
> The constructor function's parameters are not enclosed between slashes but do use quotation marks.
 
```js
let str = 'fooexample foobar';
let regex = new RegExp('foo', 'g');
 
console.log(str.match(regex)) // [ 'foo', 'foo' ]
```
 
_________________________________________________

 
 
 
## [RegExp Methods & Propertys](#Table-of-contents)

### test()
> **Definition and Usage:**\
> The `test()` method returns `true` if it finds a match returns `true`, otherwise it returns `false`.

```js
let str = 'table football, foosball';
let regex = /foo/g;
 
console.log(retex.test(str)) // true
console.log(regex.test(str)); // true
console.log(regex.test(str)); // false
 
// lastIndex
 while (regex.test(str)) {
    console.log(regex.lastIndex);
}
```

 
### exec()
> **Definition and Usage:**\
> The `exec()` method returns the matched text if it finds a match, otherwise it returns `null`.

```js
let str = 'table football, foosball';
let regex = /foo/g;
 
console.log(regex.exec(str)); // [ 'foo', index: 6, input: 'table football, foosball', groups: undefined ]
console.log(regex.exec(str)); // [ 'foo', index: 16, input: 'table football, foosball', groups: undefined ]
console.log(regex.exec(str)); // null

// lastIndex
while (regex.exec(str)) {
    console.log(regex.lastIndex);
}
```

 
### lastIndex
> **Definition and Usage:**\
> The `lastIndex` property specifies the index at which to start the next match. \
> This property returns an integer that specifies the character position immediately after the last match found by `exec()` or `test()` methods.
>
> **Note:** This property only works if the `g` modifier is set. \
> &emsp; &ensp; This property only uses `exec()` and `test()` methods. \
> &emsp; &ensp; If `exec()` or `test()` do not find a match, then lastIndex will be set to 0.

- **Examples with test()**
```js
let str = 'table football, foosball';
// lastIndex of  9 ^      19 ^

let regex = /foo/g;

// test() returns true or false. Then lastIndex will be set to value of lastIndex 
console.log(regex.test(str)); // true
console.log(regex.lastIndex); // 9
console.log(regex.test(str)); // true
console.log(regex.lastIndex); // 19
console.log(regex.test(str)); // false
console.log(regex.lastIndex); // 0

 
while (regex.test(str)) {
    console.log(regex.lastIndex);
}
// 9, 19
```

- **Examples with exec()**
```js
let str = 'table football, foosball';
// lastIndex of  9 ^      19 ^

let regex = /foo/g;

console.log(regex.exec(str)); // [ 'foo', index: 6, input: 'table football, foosball', groups: undefined ]
console.log(regex.lastIndex); // 9
console.log(regex.exec(str)); // [ 'foo', index: 16, input: 'table football, foosball', groups: undefined ]
console.log(regex.lastIndex); // 19
console.log(regex.exec(str)); // null
console.log(regex.lastIndex); // 0


while (regex.exec(str)) {
    console.log(regex.lastIndex);
}
// 9, 19
```
 

### source
> **Definition and Usage:**\
> The source property returns the text of the RegExp pattern.
 
```js
const regex1 = /foo/ig;
console.log(regex1.source); // foo
 
const regex2 = /[A-Z]\w+/g;
console.log(regex2.source); // [A-Z]\w+
```
 
 
### flags
> **Definition and Usage:**\
> The `flags` property returns a string consisting of the `flags` of the current regular expression object.

```js
let regex = /foo/gi;
console.log(regex.flags); // gi

let regex2 = /bar/msy;
console.log(regex2.flags); // msy
```

 
### global
> **Definition and Usage:**\
> This property returns `true` if the `g` modifier is set, otherwise it returns `false`.

```js
let regex1 = /foo/g;
console.log(regex1.global); // true

let regex2 = /bar/i;
console.log(regex2.global); // false
```

 
 ### ignoreCase
> **Definition and Usage:**\
> The `ignoreCase` property indicates whether or not the `i` flag is used with the regular expression. `ignoreCase` is a read-only property of an individual regular expression instance.

```js
let regex1 = /foo/;
let regex2 = /foo/i;

console.log(regex1.test('Football')); // false
console.log(regex2.ignoreCase); // true
console.log(regex2.test('Football')); // true
```

 
### multiline
> **Definition and Usage:**\
> The `multiline` property indicates whether or not the `m` flag is used with the regular expression. `multiline` is a read-only property of an individual regular expression instance.

```js
let regex1 = /^football/;
let regex2 = /^football/m;

console.log(regex1.multiline); // false
console.log(regex2.multiline); //true

console.log(regex1.test('rugby\nfootball')); // false
console.log(regex2.test('rugby\nfootball')); // true
```
 
 
### hasIndices
> **Definition and Usege:**\
> The `hasIndices` property indicates whether or not the `d` flag is used with the regular expression. `hasIndices` is a read-only property of an individual regular expression instance.

```js
let str1 = 'foo bar foo';
let regex1 = /foo/gd;

console.log(regex1.hasIndices); // Output: true
console.log(regex1.exec(str1).indices); // [ [ 0, 3 ], groups: undefined ]
console.log(regex1.exec(str1).indices); // [ [ 8, 11 ], groups: undefined ]

let str2 = 'foo bar foo';
let regex2 = /foo/;

console.log(regex2.hasIndices); // false
console.log(regex2.exec(str2).indices); // undefined
```

 
### dotAll
> **Definition and Usage:**\
> The `dotAll` property indicates whether or not the `s` flag is used with the regular expression. `dotAll` is a read-only property of an individual regular expression instance.
 
```js
let regex1 = /foo/s;
console.log(regex1.dotAll); // true

let regex2 = /bar/;
console.log(regex2.dotAll); // false
```


### sticky
> **Definition and Usage:**\
> Regular expression objects have a `lastIndex` property, which is used in different ways depending on the `g` (global) and `y` (sticky) flags. The `y` (sticky) flag tells the regular expression to look for a match at `lastIndex` and only at `lastIndex` (not earlier or later in the string).
 
```js
let str = 'table foot ball';

let regex = /\w+/y;
regex.lastIndex = 6;

console.log(regex.sticky) // true
console.log(regex.exec(str)) // [ 'foot', index: 6, input: 'table foot ball', groups: undefined ]
console.log(regex.exec(str)) // null
```

 
### unicode
> **Definition and Usage:**\
> The `unicode` property indicates whether or not the `u` flag is used with a regular expression. `unicode` is a read-only property of an individual regular expression instance.

```js
let regex1 = /\u{0104}/;
let regex2 = /\u{0104}/u;

console.log(regex1.unicode); // false
console.log(regex2.unicode); // true

console.log(regex1.source); // a
console.log(regex2.source); // a
```
_________________________________________________
 

 
 
## [String Methods using RegExp](#Table-of-contents)
  
### match()
> **Definition and Usage:**\
> The `match()` method searches a string for a match against a regular expression, and returns the matches, as an Array object.

```js
let str1 = 'The quick brown fox jumps over the lazy dog. It barked.'
 
let regex1 = /\wo\w/g;
console.log(str1.match(regex1)); //  ['row', 'fox', 'dog']
 
 
let str2 = 'The rain in SPAIN stays mainly in the plain';
 
let regex2 = /ain/g;
console.log(str2.match(regex2))   // [ ain, ain, ain ]
```

 
### matchAll()
> **Definition and Usage:**\
> The JavaScript String `matchAll()` method returns an iterator of results of matching a string against a regular expression.

```js
let str = 'text test text3 temp';
let regex = /te.t\d?/g;

let array = [...str.matchAll(regex)];
console.log(array);
 
for (let value of str.matchAll(regex)) {
    console.log(value);
}

/* Output:
[ 
  [ 'text', index: 0, input: 'text test text3 temp', groups: undefined ],
  [ 'test', index: 5, input: 'text test text3 temp', groups: undefined ],
  [ 'text3', index: 10, input: 'text test text3 temp', groups: undefined ]
 ]
*/
```

 
### replace()
> **Definition and Usage:**\
> The `replace()` method returns a new string with some or all matches of a pattern replaced by a replacement. The pattern can be a string or a `RegExp`, and the replacement can be a string or a `function` to be called for each match. If pattern is a string, only the first occurrence will be replaced.

```js
let str = 'The quick brown fox jumps over the lazy dog. If the dog reacted, was it really lazy?';
let regex = /dog/g;
let newstr = str.replace(regex, 'monkey');
console.log(newstr);
// output: "The quick brown fox jumps over the lazy monkey. If the dog reacted, was it really lazy?"
 
let regex2 = /(\w+)\s(\w+)/;
let str2 = 'John Smith';
let newstr2 = str2.replace(regex2, '$2, $1');
console.log(newstr2);  // Smith, John
```

 
### replaceAll()
> **Definition and Usage:**\
> The `replaceAll()` method returns a new string with all matches of a pattern replaced by a replacement. The pattern can be a string or a `RegExp`, and the replacement can be a string or a `function` to be called for each match.

 
```js
let str = 'The quick brown fox jumps over the lazy dog. If the dog reacted, was it really lazy?';

console.log(str.replace(/dog/g, 'monkey'));
// output: "The quick brown fox jumps over the lazy monkey. If the monkey reacted, was it really lazy?"


// global flag required when calling replaceAll with regex
let regex = /Dog/gi;
console.log(str.replaceAll(regex, 'ferret'));
// output: "The quick brown fox jumps over the lazy ferret. If the ferret reacted, was it really lazy?"
```

 
### search()
> **Definition and Usage:**\
> The `search()` method executes a `search` for a match between a regular expression and this String object.
 
```js
let str = 'The quick brown fox jumps over the lazy dog.';

// any character that is not a word character or whitespace
let regex = /\wo\w/g;

console.log(str.search(regex)); // 11
console.log(paragraph[paragraph.search(regex)]); // r
```

 
### split()
> **Definition and Usage:**
> The `split()` method divides a String into an ordered list of substrings, puts these substrings into an array, and returns the array.  The division is done by searching for a pattern; where the pattern is provided as the first parameter in the method's call.
 
```js
const str = 'Harry Trump ;Fred Barney; Helen Rigby ; Bill Abel ;Chris Hand'

let regex = /\s*(?:;|$)\s*/
let nameList = str.split(regex)

console.log(nameList)
// output: [ 'Harry Trump', 'Fred Barney', 'Helen Rigby', 'Bill Abel', 'Chris Hand' ]
```
_________________________________________________

 
 
 
## [Flags](#Table-of-contents)
  

### g
> **Definition and Usage:**\
> The `global` property indicates whether or not the `g` flag is used with the regular expression. `global` is a read-only property of an individual regular expression instance.
 
```js
let str = 'foo example foo bar food';

let regex = /foo/g;
console.log(str.match(regex)) // [ 'foo', 'foo', 'foo ]

let regex1 = /foo/;
console.log(str.match(regex1)) // [ 'foo' ]
```

 
### i
> **Definition and Usage:**\
> The `ignoreCase` property indicates whether or not the `i` flag is used with the regular expression. `ignoreCase` is a read-only property of an individual regular expression instance.
 
```js
let str = 'Foo example foo bar food';

let regex = /foo/ig;
console.log(str.match(regex)) // [ 'Foo', 'foo', 'foo ]

let regex1 = /foo/g;
console.log(str.match(regex1)) // [ 'foo', 'foo' ]
```

 
### m
> **Definition and Usage:**\
> The m modifier is used to perform a `multiline` match.
> The m modifier treat beginning `^` and end `$` characters to match the beginning or end of each line of a string (delimited by `\n` or `\r`), rather than just the beginning or end of the string.

```js
let str = 'foo example \nfoo bar \nfood';

let regex1 = /^foo/mg;
console.log(str.match(regex1)); // [ 'foo', 'foo', 'foo' ]

let regex2 = /^foo/g;
console.log(str.match(regex2)); // [ 'foo' ]
```
 
 
### d
> **Definition and Usage:**\
> The `hasIndices` property indicates whether or not the `d` flag is used with the regular expression. `hasIndices` is a read-only property of an individual regular expression instance.
 
```js
let str1 = 'foo bar foo';
let regex1 = /foo/gd;

console.log(regex1.hasIndices); // Output: true
console.log(regex1.exec(str1).indices); // [ [ 0, 3 ], groups: undefined ]
console.log(regex1.exec(str1).indices); // [ [ 8, 11 ], groups: undefined ]

let str2 = 'foo bar foo';
let regex2 = /foo/;

console.log(regex2.hasIndices); // false
console.log(regex2.exec(str2).indices); // undefined
```

 
### s
> **Definition and Usage:**\
> The value of `dotAll` is a Boolean and `true` if the `s` flag was used; otherwise, `false`. The `s` flag indicates that the dot special character `.` should additionally match the following line terminator 'newline' characters in a string, which it would not match otherwise: 

- **Examples 1**
```js
let str = 'foo\nbar foo example';
 
let regex1 = /foo.bar/; // without 's' flag
console.log(str.match(regex1)); // null
 
let regex2 = /foo.bar/s; // with 's' flag
console.log(str.match(regex2)); // [ 'foo\nbar' ]


```
 
- **Examples 2**
```js
let str = `<!--
comment...
-->`;
 
let regex1 = /<!--.+-->/g; // without 's' flag
console.log(str.match(regex1)); // null
 
let regex2 = /<!--.+-->/gs; // with 's' flag
console.log(str.match(regex2)); // [ '<!--\ncomment...\n-->' ]
```
 
 
### y
> **Definition and Usage:**\
> Regular expression objects have a lastIndex property, which is used in different ways depending on the `g` (global) and `y` (sticky) flags. The `y` (sticky) flag tells the regular expression to look for a match at `lastIndex` and only at `lastIndex` (not earlier or later in the string).
 
```js
let str = 'table foot ball';

let regex = /\w+/y;
regex.lastIndex = 6;

console.log(regex.sticky) // true
console.log(regex.exec(str)) // [ 'foot', index: 6, input: 'table foot ball', groups: undefined ]
console.log(regex.exec(str)) // null
```
 
 
### u
> **Definition and Usage:**\
> The `unicode` property indicates whether or not the `u` flag is used with a regular expression. `unicode` is a read-only property of an individual regular expression instance
 
```js
let regex1 = /\u{0104}/;
let regex2 = /\u{0104}/u;

console.log(regex1.unicode); // false
console.log(regex2.unicode); // true

console.log(regex1.source); // a
console.log(regex2.source); // a
```

_________________________________________________

 
 
 

## [Character classes](#Table-of-contents)
  
### • &nbsp;
> **Definition and Usage:**\
> The `.` Matches any single character except line terminators: `\n`, `\r`, `\u2028` or `\u2029`.\
> **Note:** that the m multiline flag doesn't change the dot behavior. So to match a pattern across multiple lines, the character class `[^]` can be used — it will match any character including newlines.\
> **Note:** `.` any character if with the regexp `s` flag, otherwise any except a newline `\n`.
 
```js
let str = 'That\'s hot!';
//           ^      ^
let regex = /h.t/g;
 
console.log(str.match(regex)); // [ 'hat', 'hot' ]
```
 
 
### \w
> **Definition and Usage:**\
> The `\w` metacharacter is used to find a word character.
> A word character is a character from `a-z`, `A-Z`, `0-9`, `_` including underscore character.
 
```js
let str = 'Give - 10%_100%!'
let regex = /\w/g;

console.log(str.match(regex)); // ['G', 'i', 'v', 'e', '1', '0', '_', '1', '0', '0']
```
 
 
### \W
> **Definition and Usage:**\
> The `\W` metacharacter is used to find a non-word character.
> A word character is a character from `a-z`, `A-Z`, `0-9`, `_` including underscore character.

```js
let str = 'Give - 10%_100%!'
let regex = /\W/g;

console.log(str.match(regex)) // [' ', '-', ' ', '%', '%', '!']
```
 
 
### \d
> **Definition and Usage:**\
> The `\d` metacharacter is used to find a digit from 0-9.

```js
let str = 'Give 100%!'
let regex = /\d/g;

console.log(str.match(regex)) // [ 1, 0, 0 ]
```
 

### \D
> **Definition and Usage:**\
> The `\D` metacharacter is used to find a non-digit character.
 
```js
let str = 'Give 100%!'
let regex = /\D/g;

console.log(str.match(regex)) // [ 'G', 'i', 'v', 'e', ' ', '%', '!' ]
```
 
 
### \s
> **Definition and Usage:**\
> Matches a single white space character, including space, tab, form feed, line feed, and other Unicode spaces.
> Equivalent to `[ \f\n\r\t\v\u00a0\u1680\u2000-\u200a\u2028\u2029\u202f\u205f\u3000\ufeff ]`
 
```js
let str = 'Is this \n\r\f all \t there is?'
let regex = /\s/g; 
 
console.log(str.match(regex)); 
// Outpur: [ ' ', ' ', '\n', '\r', '\f', ' ', ' ', '\t', ' ', ' ' ]
```
 
 
### \S
> **Definition and Usage:**\
> Matches a single character other than white space.
> Equivalent to `[^ \f\n\r\t\v\u00a0\u1680\u2000-\u200a\u2028\u2029\u202f\u205f\u3000\ufeff]`
 
```js
let str = 'Is this \n\r\f all \t there is?'
let regex = /\S/g; 
 
console.log(str.match(regex)); //
// Output: [ 'I', 's', 't', 'h', 'i', 's', 'a', 'l', 'l', 't', 'h', 'e', 'r', 'e', 'i', 's', '?' ]
```
 
 
### \0
> **Definition and Usage:**\
> The `\0` metacharacter is used to find `NUL` character.
 
```js
let str = 'Is this all there is?\0'
//                              ^
let regex = /\0/g; 
 
console.log(str.match(regex));  // [ '\x00' ]
```
 
 
### \n
> **Definition and Usage:**\
> The `\n` character is used to find a newline character.

```js
// The string write 2 newline. 1. newline with enter, 2. newline with `\n` character
llet str = `Is this
//                 ^
all there \nis?`
//        ^
let regex = /\n/g; 

console.log(str.match(regex));  // [ '\n', '\n' ]
```
 
 
### \f
> **Definition and Usage:**\
> The `\f` metacharacter is used to find a form feed character.
 
```js
let str = 'Is this all there is?\f'
//                              ^
let regex = /\f/g; 
 
console.log(str.match(regex));  // [ '\f' ]
```
 
 
### \r
> **Definition and Usage:**\
> The `\r` metacharacter is used to find a carriage return character.
 
```js
let str = 'Is this all there is?\r'
//                              ^
let regex = /\r/g; 
 
console.log(str.match(regex));  // [ '\r' ]
```
 
 
### \t
> **Definition and Usage:**\
> The `\t` metacharacter is used to find a tab character.
 
```js
let str = 'Is \t this all\tthere is?'
let regex = /\t/g; 
 
console.log(str.match(regex));  // [ '\t', '\t' ]
```
 
 
### \v
> **Definition and Usage:**\
> The `\v` metacharacter is used to find a vertical tab character.
 
```js
let str = 'Is \v this all\vthere is?'
let regex = /\v/g; 
 
console.log(str.match(regex));  // [ '\x0B', '\x0B' ]
```

_________________________________________________

 
 
 
  
## [Unicode Character classes](#Table-of-contents)
 
### \xxx
> **Definition and Usage:**\
> The `\xxx` character is used to find the Latin character specified by an octal number xxx.
 
```js
let str = 'Is this all there is?'
//            ^        ^
let regex = /\164/g; 
 
console.log(str.match(regex));  // [ 't', 't' ]
```
 
 
### \xdd
> **Definition and Usage:**\
> The `\xdd` character is used to find the Latin character specified by a hexadecimal number dd.
 
```js
let str = 'Is this all there is?'
//            ^        ^
let regex = /\x74/g; 
 
console.log(str.match(regex));  // [ 't', 't' ]
```

 
### \uhhhh
> **Definition and Usage:**\
> The `\udddd` character is used to find the Unicode character specified by a hexadecimal number dddd.
 
```js
let str = 'plus ➕, minus ➖, multiplication ✖️, division ➗, check ✔';
//                                                                    ^
let regex = /\u2714/g;

console.log(str.match(regex)); // [ '✔' ]
```

 
### \u{hhhhh}
> **Definition and Usage:**\
> The `\u{ddddd}` character is used to find the Unicode character specified by a hexadecimal number ddddd.\
> **Note:** Matches the unic character with the U+hhhhh only set `u` flag.
 
```js
let str = 'thumbsup 👍, happy 😀, confused 😕, sad 😂, angry 😠';
//                  ^                
let regex = /\u{1F44D}/gu;

console.log(str.match(regex)); // [ '👍' ]
```
_________________________________________________

 
 
 
  
## [Alternation](#Table-of-contents)

### ^x
> **Definition and Usage:**\
> The `^` matches the beginning of the string, or the beginning of a line if the multiline flag `m` is enabled. This matches a position, not a character.

```js
// without multiline
let str = `This is dog
//         ^
This quick fox
This look here dog`;
let regex = /^This/g;

console.log(str.match(regex)) // [ 'This' ]
```
 
```js
// with multiline
let str = `This is dog
This quick fox
This look here dog`;
let regex = /^This/gm;

console.log(str.match(regex)) // [ 'This', 'This', 'This' ]
```
 
 
### x$
> **Definition and Usage:**\
> The `$` matches the end of the string, or the end of a line if the multiline flag `m` is enabled. This matches a position, not a character.
 
```js
// without multiline
let str = `This is dog
This quick fox
This look here dog`;
let regex = /dog$/g;

console.log(str.match(regex)) // [ 'dog' ]
```
 
```js
// with multiline
let str = `This is dog
This quick fox
This look here dog`;
let regex = /dog$/gm;

console.log(str.match(regex)) // [ 'dog', 'dog' ]
```
 
 
### \bx or x\b
> **Definition and Usage:**\
> The `\b` matches a word boundary position between a word character and non-word character or position (start / end of string).

```js
let str = 'HELLO, LOOK AT YOU';
//      end => ^  ^ <= start  boundary
                           
let regex = /\bLO/g; // match boundary start
console.log(str.match(regex)); // [ 'LO' ]
                           
let regex = /LO\b/g; // match boundary end
console.log(str.match(regex)); // [ 'LO' ]                 
```

 
### \Bx or x\B
> **Definition and Usage:**\
> The `\B` matches any position that is not a word boundary. This matches a position, not a character.

```js
let str =   'HELLO, LOOK AT YOU';
//without end => ^  ^ <= without start  boundary
                           
let regex = /\BL/g; // match without word starting boundary
console.log(str.match(regex)); // [ 'L', 'L' ] 
                           
let regex = /O\B/g; // match without boundary end
console.log(str.match(regex)); // [ 'O', 'O', 'O' ]
```


### x(?=y)
> **Definition and Usage:**\
> Lookahead assertion: The `x(?=y)` quantifier matches `x` string that is followed by a after specific string `y`.
 
```js
let str = 'is this all there is lot';
// 'is' followed after  ' lot' ^
let regex = /is(?= lot)/g;

console.log(str.match(regex)); // [ 'is' ]
```
 
 
### x(?!y)
> **Definition and Usage:**\
> Negative lookahead assertion: The `x(?!y)` quantifier matches `x` string that is not followed by a after specific string `y`.

```js
let str =   'is this all there is lot';
//'is' not followed after ' lot' ^
let regex = /is(?! lot)/g;

console.log(str.match(regex)); // [ 'is', 'is' ]
```
 
 
### (?<=y)x
> **Definition and Usage:**\
> Lookbehind assertion: The `(?<=y)x` quantifier matches `x` string that is followed by a before specific string `y`.

```js
let str = 'is this all there is lot';
//             ^
// 'is' followed before 'th'
let regex = /(?<=th)is/g;
 
console.log(str.match(regex)); // [ 'is' ]
```

 
### (?<!y)x
> **Definition and Usage:**\
> Negative lookbehind assertion: The `x(?<!y)` quantifier matches `x` string that is not followed by a before specific string `y`.

```js
let str = 'is this all there is lot';
//             ^
// 'is' not followed before 'th'
let regex = /(?<=th)is/g;
 
console.log(str.match(regex)); // [ 'is', 'is' ]
```

_________________________________________________

 
 
 

## [Quantifiers](#Table-of-contents)

### x+
> **Definition and Usage:**\
> The `x+` quantifier matches the preceding item `x` 1 or more times.

```js
let str = 'HELLOOO, LOOK AT YOU';
//            ^     ^
let regex = /LO+/g; // + => 1-n 

console.log(str.match(regex)); // [ 'LOOO', 'LOO' ]
```
 
 
### x*
> **Definition and Usage:**\
> The `x*` quantifier matches the preceding item `x` 0 or more times.
 
 ```js
let str = 'HELLOOO, LOOK AT YOU';
//           ^^     ^
let regex = /LO*/g; // * => 0-n 

console.log(str.match(regex)); // [ 'L', 'LOOO', 'LOO' ]
```
 
 
### x?
> **Definition and Usage:**\
> The `x?` matches the preceding item `x` 0 or 1 times.
 
```js
let str = 'Should I write color or colour?';
let regex = /colou?r/g; // ? => 0-1
 
console.log(str.match(regex)); // [ 'color', 'colour' ]
```

 
### x|y
> **Definition and Usage:**\
> Matches either `x` or `y`. The alternatives can be of any characters.

```js
let str = 're, green, red, green, gren, gr, blue, yellow'
//             ^      ^    ^
let regex = /red|green/g;
console.log(str.match(regex)); // [ 'green', 'red', 'green' ]
```
 
 
### x{n}
> **Definition and Usage:**\
> Where `n` is a positive integer, matches exactly `n` occurrences of the preceding item `x`.

```js
let str = "100, 1000 or 100000?";
//              ^       ^
let regex = /\d{4}/g;

console.log(str.match(regex)); // [ '1000', '1000' ]
```
 
 
### x{n,}
> **Definition and Usage:**\
> Where `n` is a positive integer, matches at least `n` or more times occurrences of the preceding item `x`.
 
```js
let str = "100, 1000 or 100000?";
//              ^       ^
let regex = /\d{4,}/g;

console.log(str.match(regex)); // [ '1000', '100000' ]
```
 
 
### x{n,m}
> **Definition and Usage:**\
> Where `n` is 0 or a positive integer, `m` is a positive integer, and m > n, matches at least `n` and at most `m` occurrences of the preceding item `x`.
 
```js
let str = "100, 1000 or 100000?";
//         ^    ^       ^
let regex = /\d{3,5}/g;

console.log(str.match(regex)); // [ '100', '1000', '10000' ]
```
 
_________________________________________________

 
 
 

## [Greedy and Lazy Quantifier](#Table-of-contents)

### Greedy Definition
> Makes the preceding quantifier greedy, causing it to match as more characters as possible. By more time, quantifiers are greedy, and will match as many characters as possible.

### .+ 
> **Definition and Usage:**\
> The `.+` quantifier matches the preceding item `.` 1 or more times match last one characters. 
 
```js
let str = '<strong>Hello</strong> <em>World</em>';
//         <...................................>  match last one

let regex1 = /<.+>/g; 
console.log(str.match(regex1)); 
// output: [ '<strong>Hello</strong> <em>World</em>' ]
```
 
 
### Lazy Definition
> Makes the preceding quantifier lazy, causing it to match as few characters as possible. By default, quantifiers are greedy, and will match as many characters as less possible.

### x+? 
> **Definition and Usage:**\
> The `x+?` quantifier matches the preceding item `x` 1 or more times. And lazy is to match as few characters as possible by default. 
 
```js
let str = '<strong>Hello</strong> <em>World</em>';
//         <...................................> without lazy match last one
//         <......>     <.......> <..>     <...> with lazy match default 

let regex1 = /<.+>/g; // without lazy
console.log(str.match(regex1)); 
// output: [ '<strong>Hello</strong> <em>World</em>' ]
 
 
let regex2 = /<.+?>/g; // with lazy
console.log(str.match(regex2));
// outpur: [ '<strong>', '</strong>', '<em>', '</em>' ]
```
 
- **Same example:**
```js
let str = 'a "witch" and her "broom" is one';
let regex = /".+?"/g;
 
console.log(str.match(regex)); // [ '"witch"', '"broom"' ]
```
 
 
### x*?
> **Definition and Usage:**\
> The `x*?` quantifier matches the preceding item `x` 0 or more times. And lazy is to match as few characters as possible by default. 

```js
let str = `<!----> ... <!-- comment -->`;
//         <!--.....................--> without lazy last one
//         <!---->     <!--.........--> with lazy match default
 
let regex1 = /<!--.*-->/g; // without lazy
console.log(str.match(regex));
// output: [ '<!----> ... <!-- comment -->' ]
 
 
let regex2 = /<!--.*?-->/g; // with lazy
console.log(str.match(regex2));
// output: [ '<!---->', '<!-- comment -->' ]
```
 
### x??
> **Definition and Usage:**\
> The `x??` quantifier matches the preceding item `x` 0 times. And lazy is to match as few characters as possible by default. 
```js
let str = 'b be bee beer beers'
//           ^  ^   ^    ^
let regex = /bee??/g; 
console.log(str.match(regex)); //[ 'be', 'be', 'be', 'be' ]
```
 
_________________________________________________

 
 
 
 
## [Characters Sets & Ranges](#Table-of-contents)

### [xyz]
> **Definition and Usage:**\
> The `[xyz]` expression is used to find any character between the brackets.
 
```js
let str = 'glib jocks vex dwarves!'
//           ^   ^     ^    ^  ^
let regex = /[aeiou]/g;
 
console.log(str.match(regex)); // [ 'i', 'o', 'e', 'a', 'e' ]
```
 
 
### [a-z] or [A-Z]
> **Definition and Usage:**\
> The `[a-z]` matches a character having a character code between the two specified characters inclusive.

- **Match all lowercase characters**
```js
let str = 'I Scream For Ice Cream, is that OK?!';
let regex = /[a-z]/g;

console.log(str.match(regex));
// output: [ 'c', 'r', 'e', 'a', 'm', 'o', 'r', 'c', 'e', 'r', 'e', 'a', 'm', 'i', 's', 't', 'h', 'a', 't' ]
```

- **Match all uppercase characters**
```js
let str = 'I Scream For Ice Cream, is that OK?!';
let regex = /[A-Z]/g;

console.log(str.match(regex));
// output: [ 'I', 'S', 'F', 'I', 'C', 'O', 'K' ]
```

- **Match g to s**
```js
let str = 'abcdefghijklmnopqrstuvwxyz';
let regex = /[g-s]/g;

console.log(str.match(regex));
// output: [ 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's' ]
```

- **Match A to e**
```js
let str = 'I Scream For Ice Cream, is that OK?!'
let regex = /[A-e]/g;

console.log(str.match(regex));
// output: [ 'I', 'S', 'c', 'e', 'a', 'F', 'I', 'c', 'e', 'C', 'e', 'a', 'a', 'O', 'K' ]
```

 
### [0-9]
> **Definition and Usage:**\
> The `[0-9]` matches a digits inside the brackets can be any numbers or span of numbers from 0 to 9.
 
```js
let str = 'This image has a resolution of 1440×900 pixels.'

let regex1 = /[0-9]/g;
console.log(str.match(regex1)); 
// output: [ '1', '4', '4', '0', '9', '0', '0' ]
 
let regex2 = /[0-9]+x[0-9]+/g;
console.log(str.match(regex2)); // [ '1440x900' ]
```

- **Match 1 to 4**
```js
let str = '123456789';

let regex = /[1-4]/g;
console.log(str.match(regex)); // [ '1', '2', '3', '4' ]
```

 
### [^xyz]
> **Definition and Usage:**\
> A negated or complemented character class. That is, it matches anything that is not enclosed in the brackets.

```js
let str = 'glib jocks vex dwarves!'
//           ^   ^     ^    ^  ^
let regex = /[^aeiou]/g;
 
console.log(str.match(regex)); 
// output: [ 'g', 'l', 'b', ' ', 'j', 'c', 'k', 's', ' ', 'v', 'x', ' ', 'd', 'w', 'r', 'v', 's', '!' ]
```

 
### [^a-z]
> **Definition and Usage:**\
> A negated or complemented character class. You can specify a range of characters by using a hyphen, but if the hyphen appears as the first or last character.
 
```js
// [^a-z]
let str = 'I Scream For Ice Cream, is that OK?!';
let regex = /[^a-z]/g;

console.log(str.match(regex));
// output: [ 'I', ' ', 'S', ' ', 'F', ' ', 'I', ' ', 'C', ',', ' ', ' ', ' ', 'O', 'K', '?', '!' ]

// [^g-s]
let str2 = 'abcdefghijklmnopqrstuvwxyz';
let regex2 = /[^g-s]/g;

console.log(str2.match(regex2));
// output: [ 'a', 'b', 'c', 'd', 'e', 'f', 't', 'u', 'v', 'w', 'x', 'y', 'z' ]
```
 
 
### [\u{1F600}-\u{1F64F}]
> **Definition and Usage:**\
> The `[\u{1F600}-\u{1F64F}]` matches a unicode inside the brackets can be any unicode character or span of unicode from 1F600 to 1F64F.\
> **Note:** Matches the unic character with the U+hhhhh only set `u` flag.
 
```js
let str = 'happy 🙂, confused 😕, sad 😢, check ✅, cross ❎';
//                ^            ^        ^
let regex = /[\u{1F600}-\u{1F64F}]/gu;
 
console.log(str.match(regex)); // ['🙂', '😕', '😢']
```
_________________________________________________

 
 
 
 
## [Groups & ranges](#Table-of-contents)
 
### (x)
> **Definition and Usage:**\
> Capturing group: Matches `x` and remembers the match. Groups multiple tokens together and creates a capture group for extracting a substring or using a backreference.
 
```js
let str = 'hahaha haa hah!';
let regex = /(ha)+/g;
consloe.log(str.match(regex)); // [ 'hahaha', 'ha', 'ha' ]
 
let str2 =    'John Smith';
let regex2 = /(\w+)\s(\w+)/;
//      group   1      2
let newstr2 = str2.replace(regex2, '$2, $1'); // group 1 = '$1', group 2 = '$2'
console.log(newstr2);  // Smith, John
```
 
 
### (?:x)
> **Definition and Usage:**\
> Non-capturing group: Matches `x` but does not remember the match. Groups multiple tokens together without creating a capture group.

```js
let str =      'John Smith';
let regex = /(?:\w+)\s(\w+)/; 
//      group    x      1     
// group 1 Non-capturing
let newstr2 = str2.replace(regex2, '$2, $1'); // group 1 = '$1', '$2' not group
console.log(newstr2);  // $2, Smith
```
 
 
### (x|y)
> **Definition and Usage:**\
> Matches either `x` or `y`. It can operate within a group, or on a whole expression. The patterns will be tested in order

```js
let str = 'bad bud bod bed bid';
//          ^           ^   ^
let regex = /b(a|e|i)d/g;
console.log(str.match(regex)); // [ 'bad', 'bed', 'bid' ]
 
 
let str2 = `{ name: john, email: john@mail.com },
           { name: smith, email: smith@mail.com },
           { name: quano, email: quano@mail.com }`;
 
let regex2 = /(john|smith)(@\w+\.\w+)/g;
console.log(str2.match(regex2)); // [ 'john@mail.com', 'smith@mail.com' ]
```
 
 
### (?\<name\>x)
> **Definition and Usage:**\
> Named capturing group: Matches `x` and stores it on the groups property of the returned matches under the name specified by `<name>`. The angle brackets `< >` are required for group name.
 
```js
let str = 'display:flex'
let regex = /(?<key>\w+):(?<value>\w+)/; // without global search

let result = str.match(regex);
console.log(result.groups) // {key: display, value: flex}
 

let str2 = '2019-10-30 2020-01-01';
let regex2 = /(?<year>[0-9]{4})-(?<month>[0-9]{2})-(?<day>[0-9]{2})/g;
 
let result2 = [...str2.matchAll(regex2)];
console.log(result2[0].groups); // { year: '2019', month: '10', day: '30' }
console.log(result2[1].groups); // { year: '2020', month: '01', day: '01' }
 

let str3 = '{ name: john, email: john@mail.com }, { name: smith, email: smith@mail.com }';
let regex3 = /(?<email>\w+@\w+\.\w+)/g;

let result3 = [...str3.matchAll(regex3)]
console.log(result3[0].groups); // { email: 'john@mail.com' }
console.log(result3[1].groups); // { email: 'smith@mail.com' }
```
 
 
### \k\<name\>
> **Definition and Usage:**\
> Backreference: A back reference to the last substring matching the Named capture group specified by `<Name>`.

```js
let str = 'Sir, yes Sir.';
let regex = /(?<Sir>\w+), yes \k<Sir>/g;
 
console.log(str.match(regex));  // [ 'Sir, yes Sir' ]

 
let str2 = 'go to go';
let regex2 = /(?<go>go)\sto\s\k<go>/g;

console.log(str2.match(regex2)); // [ 'go to go' ]
```
 
 
### \N
> **Definition and Usage:**\
> Backreference: Where `N` is a positive integer. A back reference to the last substring matching the `N` parenthetical in the regular expression (counting left parentheses)
 
```js
let str = 'go to go';
let regex = /(go) to \1/g;
//     group  1       ^ 
console.log(str.match(regex)); // [ 'go to go' ]
 

let str = 'go to go, back to go';
let regex = /(go) (to) \1, back \2 \1/g;
//     group  1    2    ^        ^  ^
console.log(str.match(regex)); // [ 'go to go, back to go' ]
```

_________________________________________________

 
 
 
  
## [Unicode property escapes](#Table-of-contents)

> **Definition:** 
> Unicode property escapes Regular Expressions allows for matching characters based on their Unicode properties. A character is described by several properties which are either binary ('boolean-like') or non-binary. For instance, unicode property escapes can be used to match emojis, punctuations, letters (even letters from specific languages or scripts), etc.
>
> **Note:** For Unicode property escapes to work, a regular expression must use the `u` flag which indicates a string must be considered as a series of Unicode code points. See also RegExp.prototype.unicode.
>
> **Note:** Some Unicode properties encompasses many more characters than some character classes (such as `\w` which matches only latin letters, a to z) but the latter is better supported among browsers (as of January 2020).
 
- **Syntax**
```js
// Non-binary values
\p{UnicodePropertyValue}
\p{UnicodePropertyName=UnicodePropertyValue}

// Binary and non-binary values
\p{UnicodeBinaryPropertyName}

// Negation: \P is negated \p
\P{UnicodePropertyValue}
\P{UnicodeBinaryPropertyName}
```

 
### \p{UnicodeProperty}
> **Definition and Usage:**

```js
const sentence = 'A ticket to 大阪 costs ¥2000 👌.';

const regexpEmojiPresentation = /\p{Emoji_Presentation}/gu;
console.log(sentence.match(regexpEmojiPresentation));
// expected output: Array ["👌"]

const regexpCurrencyOrPunctuation = /\p{Sc}|\p{P}/gu;
console.log(sentence.match(regexpCurrencyOrPunctuation));
// expected output: Array ["¥", "."]

```
 
 
### \P{UnicodeProperty}
> **Definition and Usage:**

```js
let sentence = 'A ticket to 大阪 costs ¥2000 👌.';
 
let regexpNonLatin = /\P{Script_Extensions=Latin}+/gu;
console.log(sentence.match(regexpNonLatin));
// expected output: Array [" ", " ", " 大阪 ", " ¥2000 👌."]
```

[More on details this here](https://github.com/tc39/proposal-regexp-unicode-property-escapes)
 
_________________________________________________

 
 
 
  
## [Escaped Characters](#Table-of-contents)

### \
> **Definition and Usage:**\
> Indicates that the following character should be treated specially, or 'escaped'. It behaves one of two ways.
> * For characters that are usually treated literally, indicates that the next character is special and not to be interpreted literally. For example, `/b/` matches the character `b`. By placing a backslash in front of `b`, that is by using `/\b/`, the character becomes special to mean match a word boundary.
> * For characters that are usually treated specially, indicates that the next character is not special and should be interpreted literally. For example, `*` is a special character that means 0 or more occurrences of the preceding character should be matched; for example, `/a*/` means match 0 or more `a`s. To match `*` literally, precede it with a backslash; for example, `/a\*/` matches `a*`.
>
> **Note:** To match this character literally, escape it with itself. In other words to search for `\` use `/\\/`.\
> The following character have special meaning, and should be preceded by a `\` (backslash) to represent a literal character:\
  `.` `+` `*` `?` `^` `$` `(` `)` `[` `]` `{` `}` `|` `/` `\`
 
```js
//Escaped . character
let str = 'test@mail.com';
//                  ^
let regex = /@\w+\.\w+/g;
 
//Escaped ( ) character
let str2 = 'Matches a "A" character (char code 65). Case sensitive.';
//                                  ^            ^
let regex2 = /\(.+\)/g;

//Escaped \ character
let str3 = 'C:\\ProgramFiles\\nodejs'
//            ^              ^
let regex3 = /C:\\\w+\\\w+/g;
```

**Escaped \ (backslash) in regexp string**
 
```js
let str = 'test@mail.com';
//                  ^
let regex = new RegExp('@\\w+.\\w+', 'g');

let str2 = 'Matches a "A" character (char code 65). Case sensitive.';
//                                  ^            ^
let regex2 = new RegExp('\\(.+\\)', 'g');
 
let str3 = 'C:\\ProgramFiles\\nodejs'
//            ^              ^
let regex3 = new RegExp('C:\\\\\\w+\\\\\\w+', 'g');
```
 
_________________________________________________

 
 
 
## [Substitution](#Table-of-contents)

### $$
> **Definition and Usage:**\
>	Inserts a `$`

```js
let str = '1000tk';
let regex = /tk/;
let newstr = str.replace(regex, '$$');
console.log(newstr);  // 1000$
```
 
 
### $&
> **Definition and Usage:**\
> Inserts the matched substring.
 
 
### $`
> **Definition and Usage:**\
> Inserts the portion of the string that precedes the matched substring.
 
 
### $'
> **Definition and Usage:**\
> Inserts the portion of the string that follows the matched substring.
 
 
### $n
> **Definition and Usage:**\
> Where n is a positive integer less than 100, inserts the nth parenthesized submatch string, provided the first argument was a RegExp object.\
> **Note:** that this is 1-indexed. If a group n is not present (e.g., if group is 3), it will be replaced as a literal (e.g., `$3`).
 
```js
let str = 'John Smith';
let regex = /(\w+)\s(\w+)/;
let newstr = str.replace(regex, '$2, $1');
console.log(newstr);  // Smith, John
```
 
 
### $\<name\>
> **Definition and Usage:**\
> Where Name is a capturing group name. If the group is not in the match, or not in the regular expression, or if a string was passed as the first argument to replace instead of a regular expression, this resolves to a literal (e.g., `$<Name>`). Only available in browser versions supporting named capturing groups.
 
```js
let str = 'John Smith';
let regex = /(?<pastname>\w+)\s(?<lastname>\w+)/;
let newstr = str.replace(regex, '$<lastname>, $<pastname>');
console.log(newstr);  // Smith, John
```

_________________________________________________

 
 
  
## [Using variable](#Table-of-contents)

### regex in variable
> **Definition and Usage:**\
> If you want a dynamic variable in Regex, you must use a constructor object. It is better to use `` `${variable}` `` Template literals for this.\
> **Node:** Where a `\` regex is used, there two `\\` must be used. For example: `\w => \\w` `\s => \\s` `\\ => \\\\`
 
```js
let username = 'john'

let str = `{ name: john, email: john@mail.com },
           { name: smith, email: smith@mail.com },
           { name: quano, email: quano@mail.com }`;

let regex = new RegExp(`name:\\s${username}.+?(?=\\s*})`, 'g');

console.log(str.match(regex)); // [ 'name: john, email: john@mail.com' ]
```
 
 
### replace with function
> **Definition and Usage:**\
> The `replace()` method returns a new string with some or all matches of a pattern replaced by a replacement. The pattern can be a string or a `RegExp`, and the replacement can be a string or a function to be called for each match. If pattern is a string, only the first occurrence will be replaced.
 
- **Syntax**
```js
string.replace(regex, (match, g1, g2, ..., offset, string) => {
   code here... 
})
```
> **match:** The matched substring. (Corresponds to $& above.)\
> **g1, g2, ... :** The nth string found by a parenthesized capture group (including named capturing groups), provided the first argument to `replace()` was a `RegExp` object.\
> **offset:** The offset of the matched substring within the whole string being examined.\
> **string:**	The whole string being examined.
 
```js
let str = 'John Smith';
let regex = /(\w+)\s(\w+)/;
let newstr = str.replace(regex, (match, g1, g2, offset, string) => {
    console.log(match); // John Smith
    console.log(g1); // John
    console.log(g2); // Smith
    console.log(offset); // 0 (0 match position)
    console.log(string); //John Smith

    // code write here then return
    return match.toUpperCase()
});

console.log(newstr); // JOHN SMITH
```

