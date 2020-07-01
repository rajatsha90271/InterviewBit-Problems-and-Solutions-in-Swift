#  Longest Common Subsequence!
### Problem Statement:
Given two strings A and B. Find the longest common sequence ( A sequence which does not need to be contiguous), which is common in both the strings.

You need to return the length of such longest common subsequence.

You may assume no duplicate exists in the array

---
**Input Format**:

First argument is an string A.
Second argument is an string B.

---

**Output Format**:
Return the length of such longest common subsequence between string A and string B.


---
**Constraints**
1 <= |A|, |B| <= 1005

---
**Solution:**

    import Foundation

    class Solution {
        func solve(_ A: inout String, _ B: inout String) -> Int {
            var dp = Array(repeating:Array(repeating:0,count:B.count + 1),count:A.count + 1)
            var m = A.count
            var n = B.count
            var a = Array(A)
            var b = Array(B)
            for i in 0...m{
                for j in 0...n{
                    if i == 0 || j == 0{
                        dp[i][j] = 0
                    }
                    else if a[i-1] == b[j-1]{
                        dp[i][j] = 1 + dp[i-1][j-1]
                    }
                    else{
                        dp[i][j] = max(dp[i-1][j],dp[i][j-1])
                    }
                }
            }
            return dp[m][n]

        }
    }
