# CMPS 6610 Extra Credit Answers
  
In this extra credit assignment, we will test and review concepts you have learned since the midterm exam. Please add your written answers to `answers.md` which you can convert to a PDF using `convert.sh`. Alternatively, you may scan and upload written answers to a file named `answers.pdf`.

1. **Algorithmic Paradigms**

I like dynamic programming because I think it is the closest to how a human may reason when tasked with determining optimality for a complex problem.

Top down - When a person is tasked with solving a problem they have not seen before, the first thing they will do is search for already solved instances of this same problem and follow what was done before. If a prior solution does not exist, they will record their own solution so they can use it later. All human knowledge is simply memoization.

Bottom up - Most engineering projects use a bottom up approach, incrementally building on a series of steps to achieve a final result. When building a house, first the foundation must be set, then the frame constructed on top of the foundation, then the frame must be filled, walled, paneled, and insulated. All of these steps require the prior be completed, and they themselves serve as prerequisites for subsequent steps. 

2. **Divide and Conquer**

I went and looked at the divide and conquer algorithms we covered in the beginning of the course. It seems that while they all contain subproblems, the optimality of any given valid solution for a subproblem is either trivial or outright undefined. All of the sorting problems involve unique subproblems, but there is no optimality to be solved for, there is only a single correct solution to the given problem.

In Quicksort, for every iteration, a pivot is selected and all other elements are moved around it. This is a subproblem, but there is no criteria for an optimal solution since there is only a single valid solution for every iteration or collection of values. 

Even if you define one, it would be irrelevant to the operation of the algorithm, since the final solution will always be correct. No matter what optimal criterion you define, adhering to it would not make the final solution any more or less correct or 'optimal'

This does not neccesarily mean that divide and conquer problems outright violate optimal substructure property, but that sometimes the property simply has no application.

3. **Randomization**

- 3a. 

    If we substitute n log n for E[X] we have n log n / n<sup>2</sup> which simplifies to log n / n. 
    
    We now have the expression P[X >= n] <= log n / n. Which can be rewritten as O(log n / n)

    1. The probability that we will perform n<sup>2</sup> work for any given input and evaluated complexity (P[X >= a]) 
    
    2. Is within bounds of (<=)

    3. The expected runtime (E[X]) divided by the evaluted possibility (a)

- 3b.

    This expression would simplify to c / 10<sup>c</sup> which is a very small fraction for any given c > 0. 

    This implies that the concentration of work is extremely centralized around n log n with extremely small chance of significant deviation. 

    It can be expressed as being O(c / 10<sup>c</sup>) assuming c is included in the expectation. Otherwise it will be even smaller at O(1 / 10<sup>c</sup>)

4. **Greedy Algorithms**

This problem has optimal substructure because at every given timestep there is a choice which will maximize the amount of tasks completed within the overall given period of time. By greedily choosing the shortest processing times, we maximize the amount of tasks we can complete because choosing the short task will ensure we have the greatest chance to pickup another task as soon as possible.

Choosing the longer processing times introduces risk of overlap or time exhaustion, assuming these tasks are not weighted in any way the greedy criterion will be upheld by the fact that a shorter task chosen first will always yield a better completion to timestep ratio. 

To prove this, we can consider that given a schedule of unweighted tasks, if we take on a longer processing time task before a shorter one we will at best suffer no penalty, but likely incur great risk of a suboptimal ratio. But if we swap to take the shorter task, we will ensure the greatest chance of completing an optimal amount of tasks and having a good ratio.

For example: Given 10 seconds and 6 tasks of lengths: [5, 4, 1, 3, 2, 1]

If we select the chronologically presented 5 and 4 tasks first, we essentially lock ourselves into completing just 3 tasks in this time frame and incur a poor ratio of 0.33 tasks to timestep ratio.

But by scheduling the 1, 1, 3, and 2 tasks first, we harvest the most amount of tasks for our time and incur a better 0.40 task to timestep ratio.

If we were to take the longest task of 5 timesteps, we would still come to a solution, but by taking a more minimal value we can guarantee a more optimal solution due to the reduced wait time.

5. **Dynamic Programming**

In a linear recurrence where the entire graph is one big dependency, there is no parralelism capability. The graph for visualizing this will be the height of the input(n), with no width to enable parralel computation.

We can give the recurrence: 

W[i] = (W[i - 1], for all n) or in the standard form of W(n - 1) + O(n)

This gives the span of O(n) because the tree will be the size (height) of your input, with no span to help to reduce this over the iterations of the algorithm. 

For maximal span, we can consider a divide and conquer approach where every node has 2 children, and every child has a single parent.

We essentially break the input apart as much as we possibly can to maximize parralelization. By doing this, we ensure there are maximal sub-problems to distribute among our processors. This comes with the risk of increasing total work, but enables the overall problem to be computed faster given ample resource. 

A standard divide and conquer recurrence can be given in the standard form of 

W[i] = 2W <sub>n/2</sub> + O(n)

This gives the optimal span of O(log n) because the exponential increase of work will inherently cut the total depth of the tree. We create more subproblems, but increase the speed in which we can compute them by adding the extra dimension of parralellism.

6. **Graphs**

If the cycle is determined to be the one of the largest weight, it is impossible for it to be in a minimum spanning tree, because there is guaranteed to be a lighter cycle or sequence of nodes that will produce a more minimal tree, and by including the maximal cycle, you guarantee this lighter sequence will be missed.

If we were to take the lighter cycle and replace it with the heaviest, displacing all other vertices around this new artificially lightest cycle - we would eventually come to the conclusion that this was a component of the  minimum spanning tree solution. If at that point we were to reintroduce our previously removed lightest cycle, not only would it produce a more minimal spanning tree, but now any cut made along a frontier involving the largest weight cycle will be sub-optimal compared to the lighter cycle previously removed.


