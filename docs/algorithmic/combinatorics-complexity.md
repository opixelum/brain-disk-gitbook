# Combinatorics & Complexity

## Introduction

## Related domains

- **Operational research**: methods & techniques to solve problems for
**optimization**;
- **AI** (M. Minsky): software for solving problems that are easy for humans
but hard for computers (for now), like **learning**, **thinking**, ...

## 2 AI approaches

- **Weak AI**: AI is just a tool, like a calculator;
- **Strong AI**: software can re-write itself to solve any problem (AGI).

### Turing test

A human interacts with a computer and a human, and has to guess which one is the
computer (if he can't, the computer is intelligent).

Eg: when chatting with someone one WhatsApp, is it a human or a bot?

## Optimization problems

- **Objective function**: function to optimize (minimize or maximize) (eg: a
neural network);
- **Decision variables**: variables that can be changed to optimize the
objective function (eg: weights in a neural network);
- **Constraints**: conditions that must be respected (definition domain of the
decision variables).

### Optimums

In mathematical terms, an optimum is when the derivative of the objective
function is 0 (when the curve changes direction).

#### Global optimum

The best possible solution (lowest or highest value of the objective function).

#### Local optimum

The best solution in a neighborhood of the current solution.

### Metaheuristics

Family of general-purpose optimization algorithms that can be applied to a wide
range of problems, as long as we have an oracle to evaluate the objective
function.

For NP-hard problems, we can't find the global optimal solution in a reasonable 
time, but we can find a good local optimum

**When to use metaheuristics**:

- **No oracle**: we don't know the objective function (eg: neural network);
- When we face a **NP-hard problem** (eg: traveling salesman problem).

- **Local search**: start with a solution, and try to improve it by changing
  - **Naive**: try all possible changes;
  - **Simulated annealing**: try random changes, and accept bad changes with a 
    probability that decreases over time;
- **Population-based**:
  - **Genetic algorithm**: start with a population of solutions, and try to 
    improve it by selecting the best solutions and combining them.

#### Simulated annealing

- **Temperature**: probability of accepting a bad change;
- **Cooling schedule**: how the temperature decreases over time.
- **Neighborhood**: set of possible changes.
- **Oracle**: function that evaluates the objective function.

#### Genetic algorithm

1. **Initialization**: create a population of solutions;
2. Repeat until stopping criteria:
   1. **Evaluation**: evaluate the objective function for each solution;
   2. **Selection**: select the best solutions;
   3. **Crossover**: combine the selected solutions;
   4. **Mutation**: change some solutions.

### Type of problems

#### Graph questions

- **Shortest path**: find the shortest path between 2 nodes (eg: Dijsktra, A*).

#### Linear programs

- Real decision variables (simplex graphical method);
- Natural decision variables (branch & bound graphical method, Gomory cuts).

## Known problems

### Traveling salesman problem

**Complexity**: NP-Hard problem.

How to sell all my products without going twice to the same city, with the
shortest path?

- Decision variables: order of the cities;
- Objective function: minimize the distance;
- Constraints: visit each city once.

We can't solve it with deterministic algorithms.

### Integer Linear Programming (ILP)

**Complexity**: NP-Hard problem.
