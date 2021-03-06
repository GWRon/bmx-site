---
id: collections
title: Collections
sidebar_label: Collections
---

BlitzMax offers simple support for managing **collections** of objects, and for visiting each
object in a **collections** using a special form of [For]/[Next] loop.

The simplest kind of collection is an array:

```blitzmax
Local a[]=[1,2,3,4,5]
For Local k=EachIn a
    Print k
Next
```
Each iteration of such a loop will assign the next array element (starting with element 0) to the index variable
before executing the body of the loop. This allows you to **visit** each array element in turn.

It is also possible to create your own kind of collection with user defined types.

To do this, you must create a user defined type with a method named `ObjectEnumerator` which takes no parameters and
returns an object. The object returned by this method must itself have the following methods:

```blitzmax
Method HasNext:Int()        ' returns true if there's a next object
Method NextObject:Object()  ' returns the next object
```
You can then use the object in a [For]/[EachIn]/[Next] loop:

```blitzmax
Local list:TList = New TList

list.AddLast "Hello"
list.AddLast "World!"

For Local t:String = EachIn list
    Print t
Next
```

[For]: ../../api/brl/brl.blitz/#for
[Next]: ../../api/brl/brl.blitz/#next
[EachIn]: ../../api/brl/brl.blitz/#eachin
