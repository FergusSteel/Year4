We left off last week looking at a few MiniZinc models for graph colouring.  This week the plan is to:
- look at including a data file specifying a graph for those examples
- Think about and practice a few other types of problems to model (we may not get through all these):
    - coin changer 
        - (some content from https://blog.jpalardy.com/posts/problem-solving-with-minizinc/)
    - fruit shop problem
    - production planning
    - crystal maze puzzle (to start us thinking about how this works)

Some things we want to learn/practice:
- using .dzn files
- using sum
- using forall
- using enum 
- output as separate from model
- seeing all solutions


-------
## Graph colouring with input files
Let's look at one of the graph colouring solutions we looked at last time:

```
int: n;
set of int: NODE = 1..n;
int: m;
set of int: EDGE = 1..m;
array[EDGE] of NODE: from;
array[EDGE] of NODE: to;
int: k;
set of int: COLOUR = 1..k;
array[NODE] of var COLOUR: colours;

constraint forall(e in EDGE)(colours[from[e]] != colours[to[e]]);

solve minimize max(colours)
```
We can specify the graph we're working with by being specific about the size and edges in another (.dzn) file:

```
n = 5;
m = 6;
k = 4;
from = [1, 1, 2, 3, 3, 4];
to =   [2, 4, 3, 4, 5, 5];
```

To think about: what if we don't want to minimize colours, but instead just do a decision version with an input k?  What role does k play in the original version - what if we take it out?

How is the solver looking for solutions?  

----
## Coin changer
Classic problem you've probably seen in an algorithms course, and solved using dynamic programming.  

Given a list of coin denominations and a sum, give a list of coins that make up that sum.  

- Example: you have coins in the denominations: [1, 5, 10, 20] and must make up the sum 75.
    - One possible solution: 75 pennies - probably not prefered!
    - Another probably better solution: 3x20, 1x10, 1x5

I have a canned solution prepped, but have a go at discussing or coding up, using the stub:
```
int: total;
array[1..5] of int: coins = [1, 5, 10, 20, 50];

array[1..5] of var 0..100: counts;
```

Some of you have already seen the sum operator, but if not we'll see an example here.  

```
int: total = 56;
array[1..6] of int: coins[1,2,5,10,20,50];

array[1..6] of var 0..total: counts;

constraint sum(i in 1..6)(counts[i]*coins[i]) = total;

solve minimize sum(counts);
```
To think about: What if we want to add other restrictions?


----
## Production planning

We have to make products, given a supply of commodities/materials/resources. 
Each product has a demand for these commodities/materials/resources.
We have a given supply of each commodity/material/resource.
Each product has a given value.

We have an optimization problem "Maximize the value of production" and a 
decision problem "Can you meet the production target V?"

This is a real problem. The products may be "hard/tangible" things such as 
cars, phones, food etc. They might also be "soft" such as a services. A product
might even be software! And the commodities/materials/resources might be metals,
people-hours, energy, pollutants (CO2), ...

Who cares? Who cares about production planning? At what point might an endeavour
actually start planning production?
- note a few real considerations: how accurate are our measurements? can we guarantee sensibleness?  How robust are our optimisations to uncertainties of various kinds?


In this example look at computational costs of finding and proving optimality
via the optimization model and then via a sequence of decision problems.

Do we notice anything interesting with respect to finding optimal and proving optimal?
Are all problems hard?


To MiniZinc!

----
## Crystal maze puzzle 

![](https://i.imgur.com/BwRwONj.png)

Put the numbers 0 to 7 in the circles so that no two adjacent circles have consecutive numbers.

Work on this for a few minutes and note *how* you try to do it. 
Any insights into how to solve?
- often people think about what are *the most constrained* places, and what are the least constraining values
- try a guess/propagate cycle - this is the start of what we'll move onto next week: *consistency*

Let's do a worked example. <live example here>

But for now, to MiniZinc!

Important insights: 
- how do I specify that two adjacent things aren't the same number?
- how do I specify that each node gets a different number?  
    - I'll not make you investigate - there's a special all-different constraint.  

We will do a not-very-general version first.

And now actually to MiniZinc!