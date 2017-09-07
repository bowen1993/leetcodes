# Read N Characters Given Read4

## Problem Description

The API:`int read4(char *buf)`reads 4 characters at a time from a file.

The return value is the actual number of characters read. For example, it returns 3 if there is only 3 characters left in the file.

By using the`read4`API, implement the function`int read(char *buf, int n)`that readsncharacters from the file.

**Note:**  
The`read`function will only be called once for each test case.

> Companies: Facebook

## Analysis

Similar to 158

## Solution

```py
# The read4 API is already defined for you.
# @param buf, a list of characters
# @return an integer
# def read4(buf):

class Solution(object):
    def read(self, buf, n):
        """
        :type buf: Destination buffer (List[str])
        :type n: Maximum number of characters to read (int)
        :rtype: The number of characters read (int)
        """
        buf4 = [""] * 4
        endOfFile = False
        pointer = 0
        while pointer < n and not endOfFile:
            currRead = read4(buf4)
            if currRead != 4:
                endOfFile = True
            length = min(n - pointer, currRead)
            for i in range(length):
                buf[pointer] = buf4[i]
                pointer += 1
        return pointer
```



