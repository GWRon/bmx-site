---
id: svec3
title: SVec3
sidebar_label: SVec3
---

A 3-element structure that can be used to represent positions and directions in 3D-space.


## Constructors

### `Method New(x:Float, y:Float, z:Float)`

Creates a new [SVec3](../../../brl/brl.geometry/svec3) from the supplied arguments.

<br/>

## Operators

### `Method Operator+:SVec3(b:SVec3)`

Adds <b>b</b> to this vector, returning a new vector.

<br/>

### `Method Operator-:SVec3(b:SVec3)`

Subtracts <b>b</b> from this vector, returning a new vector.

<br/>

### `Method Operator*:SVec3(b:SVec3)`

Multiplies the vector by <b>b</b>, returning a new vector.

<br/>

### `Method Operator/:SVec3(b:SVec3)`

Devides the vector by <b>b</b>, returning a new vector.

<br/>

### `Method Operator-:SVec3()`

Returns a negated version of this vector.

<br/>

### `Method Operator*:SVec3(s:Float)`

Multiplies the vector by <b>s</b>, returning the new vector.

<br/>

### `Method Operator[]:Float(index:Int)`

Retrieves the x, y or z component using [0], [1] or [2] respectively.

<br/>

### `Method Operator[]=(index:Int, value:Float)`

Sets the x, y or z component using [0], [1] or [2] respectively.

<br/>

## Methods

### `Method Apply:SVec3(b:SMat3 Var)`

Applies the 3x3 matrix <b>b</b> to the vector, returning a new vector.

<br/>

### `Method Apply:SVec3(b:SMat4 Var)`

Applies the 4x4 metrix <b>b</b> to the vector, returning a new vector.

<br/>

### `Method Clamp:SVec3(minv:SVec3, maxv:SVec3)`

Returns the vector clamped between the vectors <b>minv</b> and <b>maxv</b>.

<br/>

### `Method Cross:SVec3(b:SVec3)`

Returns the Cross Product of the two vectors.

<br/>

### `Method Min:SVec3(b:SVec3)`

Returns a vector that is made from the smallest components of the two vectors.

<br/>

### `Method Max:SVec3(b:SVec3)`

Returns a vector that is made from the largest components of the two vectors.

<br/>

### `Method Lerp:SVec3(b:SVec3, t:Float)`

Linearly interpolates between two vectors.

Interpolates between this vector and <b>b</b> by the interpolant <b>t</b>.
This is commonly used to find a point some fraction of the way along a line between two endpoints (e.g. to move an object gradually between those points).


<br/>

### `Method Normal:SVec3()`

Returns the vector with a magnitude of 1.

When normalized, a vector keeps the same direction but its length is 1.0.


<br/>

### `Method Dot:Float(b:SVec3)`

Returns the dot product of two vectors.

For normalized vectors Dot returns 1 if they point in exactly the same direction, -1 if they point in completely opposite directions,
and a number in between for other cases (e.g. Dot returns zero if vectors are perpendicular).


<br/>

### `Method Length:Float()`

Returns the length of the vector.

<br/>

### `Method LengthSquared:Float()`

Returns the squared length of the vector.

Calculating the squared length instead of the length is much faster.
Often if you are comparing lengths of two vectors you can just compare their squared lengths.


<br/>

### `Method Distance:Float(b:SVec3)`

Returns the distance between the vector and <b>b</b>.

<br/>

### `Method DistanceSquared:Float(b:SVec3)`

Returns the squared distance between the vector and <b>b</b>.

<br/>

### `Method Reflect:SVec3(n:SVec3)`

Returns the vector reflected from the given plane, specified by its normal vector.

<br/>

### `Method ToString:String() Override`

Returns a [String](../../../brl/brl.blitz/#string) representation of the vector.

<br/>

