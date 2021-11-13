---
layout: book
title: Printing
permalink: /learn/quickstart/print
---

Although a `print` statements of the type
```
print *, ...
```
has been used in earlier chapters, formatted printing has not been explored.
The `*` indicates free-form, "list-directed" output.

Instead of `*`, a format specification can be specified in order to control the printing of items.
In FORTRAN 77, this was done using numbered `FORMAT` statements.
In modern Fortran, it is more common to use standard character strings.

A string format specification consists of multiple descriptors, separated by commas,
and enclosed by parentheses.

**Descriptors**

Descriptor | Description
--- | ---
`i` | Integer
`f` | Real number ("f" for float)
`e` | Exponential notation (mantissa in $[0.1, 1)$)
`es` | Scientific notation (mantissa in $[1, 10)$)
`a` | Character
`x` | Space
`/` | New line

Note that the descriptors can be used lowercase or uppercase.
