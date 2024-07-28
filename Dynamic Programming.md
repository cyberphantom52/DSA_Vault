Dynamic Programming is a method for solving a complex problem by breaking it down into a collection of simpler sub-problems, solving each of those sub-problems just once, and storing their solutions using a memory-based data structure ([[Array]], [[Hash Map]], etc.). So the next time the same sub-problem occurs, instead of recomputing its solution, one simply looks up the previously computed solution, thereby saving computation time.

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
- We look at the parameter that changes in each iteration/sub-problem and use it to index into our stored solutions. If multiple parameters are changing in a problem that means our dp structure  has to be multi dimensional. e.g for 2 changing parameters we can use 2D-array and so on.