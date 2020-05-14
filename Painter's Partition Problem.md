Problem Statement:

Given 2 integers A and B and an array of integars C of size N.

Element C[i] represents length of ith board.

You have to paint all N boards [C0, C1, C2, C3 … CN-1]. There are A painters available and each of them takes B units of time to paint 1 unit of board.

Calculate and return minimum time required to paint all boards under the constraints that any painter will only paint contiguous sections of board.

Input Format:

The first argument given is the integer A.
The second argument given is the integer B.
The third argument given is the integer array C.

Output Format:
Return minimum time required to paint all boards under the constraints that any painter will only paint contiguous sections of board % 10000003.

Constraints:

1 <=A <= 1000
1 <= B <= 10^6
1 <= C.size() <= 10^5
1 <= C[i] <= 10^6

Solution:
#  Painter's Partition Problem!
### Problem Statement:
Given 2 integers A and B and an array of integars C of size N.

Element C[i] represents length of ith board.

You have to paint all N boards [C0, C1, C2, C3 … CN-1]. There are A painters available and each of them takes B units of time to paint 1 unit of board. 
Calculate and return minimum time required to paint all boards under the constraints that any painter will only paint contiguous sections of board.

---
**Input Format**:
The first argument given is the integer A.
The second argument given is the integer B.
The third argument given is the integer array C.

---
**Output Format**:
Return minimum time required to paint all boards under the constraints that any painter will only paint contiguous sections of board % 10000003.

---
**Constraints**
1 <=A <= 1000
1 <= B <= 10^6
1 <= C.size() <= 10^5
1 <= C[i] <= 10^6

---
**Solution:**

    import Foundation


	//Input 
	//A = 4
	//B = 1
	//C = [1, 8, 11, 3,32,12,2,8,44]

	class Solution {
    func numberOfPaintersRequired(boards: [Int], timeUnits: Int) -> Int{
        var numberOfPainters = 1
        var timeRequiredToPaintEachUnit = 0
        
        for board in boards{
            timeRequiredToPaintEachUnit += board
            if timeRequiredToPaintEachUnit > timeUnits{
                numberOfPainters += 1
                timeRequiredToPaintEachUnit = board
            }
        }
        return numberOfPainters
    }
    func maxOf(boards: [Int]) -> Int{
        var max = Int.min
        for board in boards{
            if max <= board{
                max = board
            }
        }
        return max
        
    }
    func sumOf(boards: [Int]) -> Int{
        var sum = 0
        for board in boards{
            sum += board
        }
        return sum
    }
    func paint(_ A: inout Int, _ B: inout Int, _ C: inout [Int]) -> Int {
        var lowerBound = maxOf(boards: C)
        var upperBound = sumOf(boards: C)
        var result = 0
        while lowerBound <= upperBound{
            var mid = lowerBound + (upperBound - lowerBound) 	/ 2
            if numberOfPaintersRequired(boards: C, timeUnits:mid) <= A{
                result = mid
                upperBound = mid - 1
            }
            else{
                lowerBound = mid + 1
            }
            
        }
        return (result*B) % 10000003
    }
	}
