#  Count Total Set Bits
### Problem Statement:
Given a positive integer A, the task is to count the total number of set bits in the binary representation of all the numbers from 1 to A.

Return the count modulo 10^9 + 7.

---
**Input Format**:

First and only argument is an integer A.

---

**Output Format**:
Return an integer denoting the ( Total number of set bits in the binary representation of all the numbers from 1 to A )modulo 10^9 + 7.


---
**Constraints**
1 <= A <= 10^9

---
**Solution:**

    import Foundation

    class Solution {
        func solve(_ A: inout Int) -> Int {
            var i = 0
            var res = 0
            
            while (1 << i) <= A{
                
                var k = false
                var change = 1 << i
                for j in 0...A{
                    
                    if k{
                        res += 1
                    }
                    else{
                        res += 0
                    }
                    
                    if change == 1{
                        k = !k
                        change = 1 << i
                    }
                    else{
                        change -= 1
                    }
                    
                }
            
                
                i += 1
            }
            return res

        }
    }
