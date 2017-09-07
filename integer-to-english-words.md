# Integer to English Word

## Problem Description

Convert a non-negative integer to its english words representation. Given input is guaranteed to be less than 231- 1.

For example,  


```
123 -> "One Hundred Twenty Three"
12345 -> "Twelve Thousand Three Hundred Forty Five"
1234567 -> "One Million Two Hundred Thirty Four Thousand Five Hundred Sixty Seven"
```

> Companies: Microsoft, Facebook



## Analysis

translate each three digit separately. 

## Solution

```py
class Solution:
    def numberToWords(self, num):
        """
        :type num: int
        :rtype: str
        """
        self.LESS_THAN_20 = ["", "One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight", "Nine", "Ten", "Eleven", "Twelve", "Thirteen", "Fourteen", "Fifteen", "Sixteen", "Seventeen", "Eighteen", "Nineteen"]
        self.TENS = ["", "Ten", "Twenty", "Thirty", "Forty", "Fifty", "Sixty", "Seventy", "Eighty", "Ninety"]
        self.THOUSANDS = ["", "Thousand", "Million", "Billion"]
        if num == 0:
            return "Zero"
        i = 0
        words = ""
        while num > 0:
            if num % 1000 != 0:
                words = self.helper(num % 1000) + self.THOUSANDS[i] + " " + words
            num /= 1000
            i += 1
        return words.strip()

    def helper(self, number):
        if number == 0:
            return ""
        elif number < 20:
            return self.LESS_THAN_20[number] + " "
        elif number < 100:
            return self.TENS[number / 10] + " " + self.helper(number%10)
        else:
            return self.LESS_THAN_20[number / 100] + " Hundred " + self.helper(number % 100)
```





