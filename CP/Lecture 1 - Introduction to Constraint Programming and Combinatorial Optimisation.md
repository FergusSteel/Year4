- What is Combinatorial Optimisation?
	- Discrete problems, optimisation finds a solution that optimises some characteristics.
	- Decision asks if it can be done?
		- Decision versions are important forma  complexity perspective
	- Basically trying to find an optimal object from a finite set of objects.
- Solver Types
	- Many types of general; solvers, often go along with expressing the problem in particular ways.
		- CP solvers based on search
		- SAT solvers
		- IP solvers
		- SIMPLEX
		- Not-guaranteed-to-be-optimal heuristic solvers
	-  Example solver approach: (Exhaustive) Combinatorial search
		- To get started with search-based approaches, let's talk about a naive approach to combinatorial search
			- we'll do it via an example of max clique
			- we'll draw a search tree, etc.

- Constraint Programming
	- A Constraint Program, is a framework for solving constraint satisfaction problem (a CSP)
	- A CSP is a triple consisting of:
		- Variables
		- Domains for those variables
		- Constraints
	- Often we'd denote those as $(X, D, C)$ i.e. variables, domains and constraints
	- Example: Graph colouring on graph $G = (V, E)$:
		- Variables: $\{c_v |  v \in V\}$ - colour for each vertex
		- Domains: $\{1, 2, ... k\}$ - all the colours
		- Constraints: when $(u, v) \in E$ then $c_u \neq c_v$
	- What are constraints?
		- One way to formally view a constrain is a pair $C = (S,R)$$ where $S = (x_i, ..., x_{i_K})$ are the variables the constraint is about (i.e. the scope) and $R$ are the tuples that satisfy the constraint
			- I.e. $R \subset d_i \times d_{i_k}$
		- For many kinds of constraints this would be a big ass set, and so we often specify constraints in a more compact way.
	- Solutions:
		- We are sometimes interested in different notions of *solution*.  We'll touch on these as we go and have already brushed up against them, but for now note that sometimes we want:
			- all solutions
			- a single solution (decision?)
			- the cheapest solution (optmisation?)
		- 