---
layout: book
title: Printing
permalink: /learn/quickstart/print
---

Although `print` statements of the type
```
print *, ...
```
has been used in earlier chapters, formatted printing has not been explored.
The `*` indicates free-form, "list-directed" output.
The `...` represents "list items", separated by `,`s.

Instead of `*`, a format specification can be specified in order to control the printing of items.
In FORTRAN 77, this was done using numbered `FORMAT` statements.
In modern Fortran, it is more common to use standard character strings.

A string format specification consists of multiple items, separated by commas,
and enclosed by parentheses.
The items can be
- descriptors (individual format specifications expressing how to format a certain value or set of values)
- string literals (quoted)

Example:
```fortran
print '("x = ", e11.4)', x
```

## Field descriptors

Descriptor | Description
--- | ---
`i` | Integer
`f` | Real number ("f" for float)
`e` | Exponential notation (mantissa in [0.1, 1))
`es` | Scientific notation (mantissa in [1, 10))
`g` | Automatically chooses between `f` and `e` formats
`a` | Character
`x` | Space
`/` | New line

Note that the descriptors can be used lowercase or uppercase.

Examples of each follow.

### `i` -- Integer

Unformatted:
```fortran
integer :: n
n = 2

print *, n
```
```
           2
```
👆 The `2` in the output is in column 12.
For the largest 32-bit integer (2,147,483,647) this format leaves two spaces to the left.

An integer following the `i` specifies the field width.
Using `0`, the full integer is printed and left-aligned.
```fortran
print '(i0)', n
```
```
2
```

Integers are right-aligned in their field when the width is nonzero.
```fortran
print '(i4)', n
```
```
   2
```

When the field width is too small for the integer to be shown in full, `*` are shown instead
(at least with `gfortran`).
```fortran
print '(i2)', n * 100
```
```
**
```

`i` also supports the format `i<field width>.<minimum digits>`.
Field width must be specified.
When the integer's number of digits is smaller than the minimum, it becomes zero-padded.
```fortran
print '(i0.3)', n
print '(i4.3)', n
print '(i4.3)', n * 100
```
```
002
 002
 200
```


## Combining

...

## Misc.

Empty line:
```fortran
print *
```

Any individual format spec can be repeated by prefixing an integer.
```fortran
print '(2a)', 'For', 'tran'
```
```
Fortran
```

Groups can be repeated by surrounding the group in parentheses and prefixing an integer.

If there are more list items than format specs, it will end the line and then cycle/reuse the format.
```fortran
print '(a)', 'For', 'tran'
```
```
For
tran
```
