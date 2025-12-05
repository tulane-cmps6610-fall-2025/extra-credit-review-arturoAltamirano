# CMPS 6610 Extra Credit Answers
  
In this extra credit assignment, we will test and review concepts you have learned since the midterm exam. Please add your written answers to `answers.md` which you can convert to a PDF using `convert.sh`. Alternatively, you may scan and upload written answers to a file named `answers.pdf`.

1. **Algorithmic Paradigms**

I like dynamic programming because I think it is the closest to how a human may reason when tasked with determining optimality for a complex problem.

Top down - When a person is tasked with solving a problem they have not seen before, the first thing they will do is search for already solved instances of this same problem and follow what was done before. If a prior solution does not exist, they will record their own solution so they can use it later. All human knowledge is simply memoization.

Bottom up - Most engineering projects use a bottom up approach, incrementally building on a series of steps to achieve a final result. When building a house, first the foundation must be set, then the frame constructed on top of the foundation, then the frame must be filled, walled, paneled, and insulated. All of these steps require the prior be completed, and they themselves serve as prerequisites for subsequent steps. 

2. **Divide and Conquer**

I went and looked at the divide and conquer algorithms we covered in the beginning of the course. It seems that while they all contain subproblems, the optimality of any given valid solution for a subproblem is either trivial or outright undefined. 

In Quicksort, for every iteration, a pivot is selected and all other elements are moved around it. This is a subproblem, but there is no criteria for an optimal solution since there is only a single valid solution for every iteration or collection of values. 

Even if you define one, it would be irrelevant to the operation of the algorithm, since the final solution will always be correct.

This does not neccesarily mean that divide and conquer problems outright violate optimal substructure property, but that sometimes the property simply has no application.

3. **Randomization**

- 3a. 

- 3b.

4. **Greedy Algorithms**

5. **Dynamic Programming**

6. **Graphs**
