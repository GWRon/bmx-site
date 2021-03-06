---
id: strings
title: Strings
sidebar_label: Strings
---

Strings are used to store sequences of characters.

Strings are actually objects, so can be used where ever an object is expected.
Strings provide the following methods:

| Method | Description |
|---|---|
| `Find:Int( subString:String,startIndex=0 )` | Finds first occurance of a sub string. Returns -1 if **subString** not found. |
| `FindLast:Int( subString:String,startIndex=0 )` | Finds last occurance of a sub string. Returns -1 if **subString** not found. |
| `Trim:String()` | Removes leading and trailing non-printable characters from a string. |
| `Replace:String( subString:String,withString:String )` | Replaces all occurances of **subString** with **withString**. |
| `StartsWith:Int( subString:String )` | Returns true if string starts with **subString**. |
| `EndsWith:Int( subString:String )` | Returns true if string ends with **subString**. |
| `Contains:Int( subString:String )` | Returns true if string contains **subString**. |
| `Join:String( bits:String[] )` | Joins **bits** together by inserting this string between each bit. |
| `Split:String[]( separator$[] )` | Splits this string into bits delimited by **separator**. |
| `ToLower:String()` | Converts string to lowercase. |
| `ToUpper:String()` | Converts string to uppercase. |
| `ToInt:Int()` | Converts string to an integer. |
| `ToLong:Long()` | Converts string to a long. |
| `ToFloat:Float()` | Converts string to a float. |
| `ToDouble:Double()` | Converts string to a double. |
| `ToCString:Byte Ptr()` | Converts string to a null terminated sequence of 8 bit bytes. The returned memory must eventually be freed with a call to [MemFree]. |
| `ToWString:Short Ptr()` | Converts string to a null terminated sequence of 16 bit shorts. The returned memory must eventually be freed with a call to [MemFree]. |

Strings also provide a read-only length field.

Here is an example of using string methods:
```blitzmax
Local t:String="***** HELLO *****"

Print t.length			'return length of string: 17
Print t.Find( "HE" )		'returns index of substring "HE": 6
Print t.Replace( "*","!" )	'replaces all "*" with "!"
Print t.ToLower()		'coverts string to lowercase
Print ":".Join( ["Hello","World"] )	'returns "Hello:World"
```

String also provide the following functions to help with the creation of strings:

| Function | Description |
|---|---|
| `FromInt:String( value:Int )` | Creates a string from an integer. |
| `FromLong:String( value:Long )` | Creates a string from a long. |
| `FromFloat:String( value:Float )` | Creates a string from a float. |
| `FromDouble:String( value:Double)` | Creates a string from a double. |
| `FromCString:String( cString:Byte Ptr )` | Creates a string from a null terminated sequence of 8 bit bytes. |
| `FromWString:String( wString:Short Ptr )` | Creates a string from a null terminated sequence of 16 bit shorts. |
| `FromBytes:String( bytes:Byte Ptr,length )` | Creates a string from a sequence of length 8 bit bytes. |
| `FromShorts:String( shorts:Short Ptr,length )` | Creates a string from a sequence of length 16 bit shorts. |


To call a string function, use: String.Function - for example:

```blitzmax
Print String.FromInt( 10 )
```

[MemFree]: ../../api/brl/brl.blitz/#memfree
