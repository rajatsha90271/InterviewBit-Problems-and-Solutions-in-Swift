#  Rotated Sorted Array Search!
### Problem Statement:
Given an array of integers A of size N and an integer B.

array A is rotated at some pivot unknown to you beforehand.

(i.e., 0 1 2 4 5 6 7 might become 4 5 6 7 0 1 2 ).

You are given a target value B to search. If found in the array, return its index, otherwise return -1.

You may assume no duplicate exists in the array
---
**Input Format**:
The first argument given is the integer array A.
The second argument given is the integer B.

---
**Output Format**:
Return index of B in array A, otherwise return -1
---
**Constraints**
1 <= N <= 1000000
1 <= A[i] <= 10^9
all elements in A are disitinct.

---
**Solution:**

 import Foundation

class Solution {
    func search(_ A: [Int], _ B: inout Int) -> Int {
        var left = 0
        var right = A.count - 1
        while left <= right{
            var mid = left + (right - left) / 2
            
            if A[mid] == B{
                return mid
            }
            if A[left] <= A[mid]{
                if B >= A[left] && B <= A[mid]{
                    right = mid - 1
                }
                else{
                    left = mid + 1
                }
                
            }
            else{
                if B >= A[mid] && B <= A[right]{
                    left = mid + 1
                }
                else{
                    right = mid - 1
                }
            }
            
            
        }
        return -1
    }
}
