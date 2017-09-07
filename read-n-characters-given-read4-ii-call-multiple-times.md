# Read N Characters Given Read4 II - Call multiple times

## Problem Description

The API:`int read4(char *buf)`reads 4 characters at a time from a file.

The return value is the actual number of characters read. For example, it returns 3 if there is only 3 characters left in the file.

By using the`read4`API, implement the function`int read(char *buf, int n)`that readsncharacters from the file.

**Note:**  
The`read`function may be called multiple times.

> Companies: Google, Facebook, Bloomberg

## Analysis

read 4 each time with read4 api. and track how much we read and how much left.

## Solution

```py
# The read4 API is already defined for you.
# @param buf, a list of characters
# @return an integer
# def read4(buf):

class Solution(object):
    buf4ptr = 0
    buf4cnt = 0
    buf4 = [""]*4
    def read(self, buf, n):
        """
        :type buf: Destination buffer (List[str])
        :type n: Maximum number of characters to read (int)
        :rtype: The number of characters read (int)
        """
        pointer = 0
        while pointer < n:
            if self.buf4ptr == 0:
                self.buf4cnt = read4(self.buf4)
            if self.buf4cnt == 0:
                break
            while pointer < n and self.buf4ptr < self.buf4cnt:
                buf[pointer] = self.buf4[self.buf4ptr]
                pointer += 1
                self.buf4ptr += 1
            if self.buf4ptr >= self.buf4cnt:
                self.buf4ptr = 0
        return pointer
```



