---
id: variables
title: Variables
sidebar_label: Variables
---

Variables are used to store values that change during the execution of your program.

Variables should be declared in your program before use. Declaring a variable means defining a name and type for the
variable and, optionally, an initial value.

The general syntax for declaring a variable is:

```
Declaration Identifier : Type = Expression
```
Multiple variables may be declared in one statement using the comma separator.

In [Strict] mode, if the type of a variable is omitted, the variable defaults to being of type [Int]. In [SuperStrict]
mode the type is mandatory. If the initial value expression is omitted, the variable is assigned an initial value of
[Null].

There are 3 kinds of variable, each of which differs by how and where the variable is stored:

## Local Variables

Local variables are used to store temporary values that will eventually be discarded. Local variables are associated
with the block of code they are declared in, and are only visible to code within that block. A block of code is
represented by one of the following:

* The body of a function or loop

* The body of an if/then/else statement

* The body of a case or default statement


To declare a local variable, use a [Local] declaration:

```blitzmax
Local int_var
Local string_var:String = "Str", float_var:Float = 10.5
```

## Global Variables

Global variables are variables that exist for the entire lifetime of a program.

To declare a global variable, use a [Global] declaration:

```blitzmax
Global int_var
Global string_var:String = "Str", float_var:Float = 10.5
```
## Field Variables

Field variables are declared within user-defined types using a [Field] declaration:

```blitzmax
Field int_var
Field string_var:String = "Str", float_var:Float = 10.5
```
See the user-defined types section for more on field variables.

## Assigning variables

Once declared, a variable's value may be changed using an assignment statement:

```blitzmax
Variable = Expression
```
You can also perform **modifying** assignments, which are shorthand for `Variable = Variable Operator Expression`.
The syntax for modifying assignments is:

| Syntax | Operator |
|---|---|
| `:+`  | Addition  |
| `:-`  | Subtraction  |
| `:*`  | Multiplication  |
| `:/`  | Division  |
| `:Mod`  | Remainder  |
| `:&`  | Bitwise and  |
| <code>:&#124;</code>  | Bitwise or  |
| `:~`  | Bitwise exclusive or  |
| `:Shl`  | Bitwise shift left  |
| `:Shr`  | Bitwise shift right  |
| `:Sar`  | Arithmetic shift right  |

For example, the code `my_var :+ 1` can be used in place of `my_var = my_var + 1`.

[Int]: ../../api/brl/brl.blitz/#int
[Null]: ../../api/brl/brl.blitz/#null
[SuperStrict]: ../../api/brl/brl.blitz/#superstrict
[Local]: ../../api/brl/brl.blitz/#local
[Global]: ../../api/brl/brl.blitz/#global
[Field]: ../../api/brl/brl.blitz/#field
