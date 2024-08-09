Dynamic Programming is a method for solving a complex problem by breaking it down into a collection of simpler sub-problems, solving each of those sub-problems just once, and storing their solutions using a memory-based data structure ([[Array]], [[Hash Map]], etc.). So the next time the same sub-problem occurs, instead of recomputing its solution, one simply looks up the previously computed solution, thereby saving computation time. This also means that DP is not helpful for problems where there are no overlapping sub-problems i.e same sub-problem doesn't occur multiple times.

## ELI5 for DP
>\*writes down "1+1+1+1+1+1+1+1 =" on a sheet of paper\*  
>"What's that equal to?"  
>\*counting\* "Eight!"  
>\*writes down another "1+" on the left\*  
>"What about that?"  
>\*quickly\* "Nine!"  
>"How'd you know it was nine so fast?"  
>"You just added one more"  
>"So you didn't need to recount because you remembered there were eight! Dynamic Programming is just a fancy way to say 'remembering stuff to save time later'"

#### Tips:
- We look at the parameter that changes in each iteration/sub-problem and use it to index into our stored solutions. If multiple parameters are changing in a problem that means our Dynamic Programming structure has to be multi dimensional. e.g for 2 changing parameters we can use 2D-array and so on.

## DP on Sub-sequences
For DP on sub-sequences, first we see how to generate all sub sub-sequences. In other words how to generate all possible combinations of given data. For this see [[Recursion and Backtracking]].

Generating all sub-sequences itself can't be optimized by DP as there are no overlapping sub-problems but when additional constrains are provides such as [Partition Equal Subset Sum](https://leetcode.com/problems/partition-equal-subset-sum/). Then DP becomes applicable.

Generally for DP on sub-sequences our DP structure is 2 dimensional. One of these dimensions comes from subset/sub-sequence generation (i.e the index up-to which the input is considered for a sub-problem) and the other comes from the additional constrain that the problem provides. e.g In case of the problem mentioned above we define our DP as
$$dp = vec![vec![false; 1 + sum];\ nums.len()]$$then **`dp[i][j]`** represents "Is there a subset up-to index $i$ whose sum is equal to $j$ ."

This pattern can be extended to solve most DP on Sub-sequence problems.

