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

### Metaheuristics

Family of general-purpose optimization algorithms that can be applied to a wide
range of problems, as long as we have an oracle to evaluate the objective
function.

**When to use metaheuristics**:

- **No oracle**: we don't know the objective function (eg: neural network);
- When we face a **NP-hard problem** (eg: traveling salesman problem).

- **Local search**: start with a solution, and try to improve it by changing
  - **Naive**: try all possible changes;
  - **Recuit simulé**: try random changes, and accept bad changes with a 
    probability that decreases over time;
- **Population-based**:
  - **Genetic algorithm**: start with a population of solutions, and try to 
    improve it by selecting the best solutions and combining them.

### Type of problems

#### Graph questions

- **Shortest path**: find the shortest path between 2 nodes (eg: Dijsktra, A*).

#### Linear programs

- Real decision variables (simplex graphical method);
- Natural decision variables (branch & bound graphical method, Gomory cuts).
