---
id: interfacing_with_c
title: Interfacing With C
sidebar_label: Interfacing With C
---

You can use the [Import] command to add certain non-BlitzMax source files to your projects,
and the [Extern] command to make the functions in those files available to BlitzMax applications.

The currently supported non-BlitzMax source file types are: .c (C); .cpp (C++); .cxx (C++); .m (ObjectiveC); and .s (Assembler).

BlitzMax will use the GNU compiler tools to compile C, C++ and ObjectiveC files, and
either the 'fasm' assembler for x86 assembly or GNU assembler for PowerPC assembly.

Here is a simple example of importing C source code into your project and accessing a C function:
```c
//----- file: c_funcs.c -----
int Doubler( int x ){
	return x+x;
}
```

```blitzmax
'----- file: app.bmx -----
Import "c_funcs.c"

Extern
	Function Doubler( x )
End Extern

Print Doubler(10)
```

You can also use [Import] to add a C compiler 'include' directory. To do this, use an import path
that ends in "*.h", for example:

```blitzmax
Import "include/*.h"
```

[Extern] can also be used to work with C++ style objects from within BlitzMax. To do this,
simply place a user-defined type declaration within an extern block. For example:
```c
//----- file: mytype.cpp -----
#include

class MyType{
public:
	virtual ~MyType(){}
	virtual void Test(){ printf( "Hello World!\n" ); }
};

extern "C"{

MyType *CreateMyType(){
	return new MyType;
}

void DestroyMyType( MyType *t ){
	delete t;
}
```

```blitzmax
'----- File: app.bmx -----
Import "mytype.cpp"

Extern

Type TMyType
	Method _pad1()	'padding for virtual destructors
	method _pad2()
	Method Test()
End Type

Function CreateMyType:TMyType()
Function DestroyMyType( t:TMyType )

End Extern

Local t:TMyType=CreateMyType()
t.Test
DestroyMyType t
```

Note that there are several limits on the use of extern types:

* Methods declared in an extern type must be declared virtual in the C++ class.
* Objects of extern type cannot be created with [New]. Instead, such objects must be created by an extern function.
* Extern types can extend other extern types, but can not extend standard BlitzMax types. Similarly, BlitzMax types can not extend extern types.
* Objects of extern type cannot be cast to 'Object'.

[Import]: ../../api/brl/brl.blitz/#import
[Extern]: ../../api/brl/brl.blitz/#extern
[New]: ../../api/brl/brl.blitz/#new
