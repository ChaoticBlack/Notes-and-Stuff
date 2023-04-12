
## 6 steps to go through DP Problems
1. Identify the category of the problem
	1. 0/1 Knapsack
	2. Unbounded Knapsack
	3. Shortest Path
	4. Fibonacchi Sequence
	5. Longest Common subsequence

2. States
	What variables do we need to keep track of in order to reach our optimal result? [www.quora.com/What-does-a-state-represent-in-terms-of-Dynamic-Programming](http://www.quora.com/What-does-a-state-represent-in-terms-of-Dynamic-Programming)

3. Decisions
	What decisions will get me closer to the base case and lead us towards the question we want to answer. 

4. Base Case
	Base cases need to relate directly to the conditions required by the answer we are seeking. This is why it is important for our decisions to work towards our base cases, as it means our decisions are working towards our answer.

5. Code

6. Optimize
	Once we introduce memoization, we will only solve each subproblem ONCE. We can remove recursion altogether and avoid the overhead and potential of a stack overflow by introducing tabulation

https://leetcode.com/problems/target-sum/solutions/455024/dp-is-easy-5-steps-to-think-through-dp-questions/?orderBy=most_votes
