# Meeting Rooms II

## Problem Description

Given an array of meeting time intervals consisting of start and end times`[[s1,e1],[s2,e2],...]`\(si&lt; ei\), find the minimum number of conference rooms required.

For example,  
Given`[[0, 30],[5, 10],[15, 20]]`,  
return`2`.

## Analysis

This problem can be solved with sorting or heap \(kind of the same thing\)

**Heap**

sort intervals with start time.

put intervals into heap, sorting based on end time.

put first started interval into heap \(as ongoing meeting\).

for next started interval, first pull interval in heap, compare end time. if new interval start time bigger than ongoing meeting, it is okay and just update current ongoing meeting end time. else, put new interval into heap. put pulled interval back.

**without heap**





