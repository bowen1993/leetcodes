# ZigZag Conversion

## Problem Description

The string`"PAYPALISHIRING"`is written in a zigzag pattern on a given number of rows like this: \(you may want to display this pattern in a fixed font for better legibility\)

```
P   A   H   N
A P L S I I G
Y   I   R
```

And then read line by line:

`"PAHNAPLSIIGYIR"`

Write the code that will take a string and make this conversion given a number of rows:

```
string convert(string text, int nRows);
```

`convert("PAYPALISHIRING", 3)`

should return

`"PAHNAPLSIIGYIR"`

.

## Analysis

The idea is to use the remainder \(index%period\) to determine which line the character at the given index will be. The period is calculated first based on nRows. A dictionary with remainder:line as key:value is then created \(this can also be done with a list or a tuple\). Once these are done, we simply go through s, assign each character to its new line, and then combine these lines to get the converted string.





