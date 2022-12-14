---
title: String
category: 'inner'
tags: [object]
---

<!--constructor--> 
<!--1--> 

### String.constructor(str)

::i-chinese{sha="cadd2a45f0d06386d13d1753c48229d2df06f1effb56a77193a789cbf969dd6c"}
::
Create a new String

<!--21--> 

### String.prototype.charAt(pos)

::i-chinese{sha="0654ea566dccfc84edcc59f6a055d0b9e0d0829a01a3c3212bdcf92062b6284b"}
::
Return a single character at the given position in the String.

### String.prototype.charCodeAt(pos)

::i-chinese{sha="59f5efb12dee7c7b1cbb1b76f91f361c4e1cab7e6103f27a3201f5e3864f5781"}
::
Return the integer value of a single character at the given position in the
String.

Note that this returns 0 not 'NaN' for out of bounds characters

### String.prototype.concat(args)

::i-chinese{sha="69e7e6e917f60c03ff89d257c51d49f0aa1d2009c2f3d944a7813fa9ed3550af"}
::
Append all arguments to this `String` and return the result. Does not modify the
original `String`.

### String.prototype.endsWith(searchString,length)

::i-chinese{sha="1d3b593a9d9057fdf7ba78db3ac8456e0ef4d4fca29367f013ab566ad2a9122c"}
::
`true` if the given characters are found at the end of the string, otherwise, `false`.

### String.prototype.includes(substring,fromIndex)

::i-chinese{sha="02defdc67dedc29113d74d8959a6bc85006a9145829bf70ab04d39ce8fab3672"}
::
`true` if the given characters are in the string, otherwise, `false`.

### String.prototype.indexOf(substring,fromIndex)

::i-chinese{sha="e6220f1abcfa1619b0dab2a4c489c72e74d95ea5b78f090adf8f2483015446bb"}
::
Return the index of substring in this string, or -1 if not found

### String.prototype.lastIndexOf(substring,fromIndex)

::i-chinese{sha="09b8d6b1322b852999cec2f949f2cfc8ed221f16155ceeb9e87839375a5ce853"}
::
Return the last index of substring in this string, or -1 if not found

### String.prototype.length

::i-chinese{sha="bc84dcc22456aa799fe344f90fce927e95cd82a89060498e0b1cd9eda4f6ca7b"}
::
Find the length of the string

### String.prototype.match(substr)

::i-chinese{sha="68332f2e6819c0c635e945309814062e61e79d3426d8c16a2b3e73a37a8d6049"}
::
Matches an occurrence `subStr` in the string.

Returns `null` if no match, or:

```javascript
"abcdef".match("b") == [
  "b",         // array index 0 - the matched string
  index: 1,    // the start index of the match
  input: "b"   // the input string
 ]
"abcdefabcdef".match(/bcd/) == [
  "bcd", index: 1,
  input: "abcdefabcdef"
 ]
```

'Global' RegExp matches just return an array of matches (with no indices):

```javascript
"abcdefabcdef".match(/bcd/g) = [
  "bcd",
  "bcd"
 ]
```

### String.prototype.padEnd(targetLength,padString)

::i-chinese{sha="1e16147b48891df9d28979fd914dcf0cf5e4bbd019b57df1ac7b293261ef45cc"}
::
Pad this string at the end to the required number of characters

```
"Hello".padEnd(10) == "Hello     "
"123".padEnd(10,".-") == "123.-.-.-."
```

### String.prototype.padStart(targetLength,padString)

::i-chinese{sha="133b8cbf2d1c26cc0e55ac68d9f8d8630fe8318f7585d2063ea48ed8d502c575"}
::
Pad this string at the beginning to the required number of characters

```
"Hello".padStart(10) == "     Hello"
"123".padStart(10,".-") == ".-.-.-.123"
```

### String.prototype.repeat(count)

::i-chinese{sha="0d88630fa1e46042c42618b96194a3dce206643ac37422c4de86ad3892c25c2d"}
::
Repeat this string the given number of times.

### String.prototype.replace(subStr,newSubStr)

::i-chinese{sha="5f652521d46d4c0d44fea25546644f38acd3d9a83a50b3cc9137f75f9c548361"}
::
Search and replace ONE occurrence of `subStr` with `newSubStr` and return the
result. This doesn't alter the original string. Regular expressions not
supported.

### String.prototype.slice(start,end)

::i-chinese{sha="638f6108a536438c55fc1ce3d5fc67eb63d71781d55e593b410e1119598c458c"}
::
Part of this string from start for len characters

### String.prototype.split(separator)

::i-chinese{sha="470ecbf00a153a1f97cb4a7c25810673778807c0b7509ec26567b36e4763288b"}
::
Return an array made by splitting this string up by the separator. eg. `'1,2,3'.split(',')==['1', '2', '3']`

Regular Expressions can also be used to split strings, e.g. `'1a2b3
4'.split(/[^0-9]/)==['1', '2', '3', '4']`.

### String.prototype.startsWith(searchString,position)

::i-chinese{sha="70841fa22587d6a8d3f02aafa420265ec9be1a94a73be747e429ad66060b19d3"}
::
`true` if the given characters are found at the beginning of the string, otherwise, `false`.

### String.prototype.substr(start,len)

::i-chinese{sha="638f6108a536438c55fc1ce3d5fc67eb63d71781d55e593b410e1119598c458c"}
::
Part of this string from start for len characters

### String.prototype.substring(start,end)

::i-chinese{sha="3bfbc2f4d21232638b4baef85264b5bfa04f0ed31cc64bc70324b8a369536e69"}
::
The part of this string between start and end

### String.prototype.toLowerCase()

::i-chinese{sha="6bd5889e69c444de0b21a33bf64f6b599f25f864131b23f9cc64716a543531e0"}
::
The lowercase version of this string

### String.prototype.toUpperCase()

::i-chinese{sha="4cacf040f5271aa6e6d9c62b618a4e0af95c04fa88d21a8daafb2890bc1fbc8f"}
::
The uppercase version of this string

### String.prototype.trim()

::i-chinese{sha="165f662450f04a169439ffd984d17af6827a7e1d6b0ad90cc1f5d6eb8d9df5e2"}
::
Return a new string with any whitespace (tabs, space, form feed, newline,
carriage return, etc) removed from the beginning and end.

<!--1--> 

### String.fromCharCode(code)

::i-chinese{sha="c9b65d538eff04e3d077070139acdeb29ce1305946f83192c42867f53aa439b3"}
::
Return the character(s) represented by the given character code(s).
