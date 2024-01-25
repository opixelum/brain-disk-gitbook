# Linear Programming

## Graphical Method

## Simplex Algorithm

### Table Method

- Faster than the equation method (less verbose);
- Less semantically clear than the equation method;
- `Z` column must only contain `0`'s or `1`'s;
- We chose the pivot col by selecting the most negative value in the `Z` row;
- The algorithm stops when the `Z` row contains only positive values;
- Rows "labels" contain only the positive decision variables.

1. Add the decision variables to the table;
2. Find the evident solution with the decision variables = 0; When we don't
  have an evident solution (all decision variables = 0), we add an artificial
  variable to the table.
  Then, we try to find a solution where the artificial variable = 0, and once we
  find it, we continue the algorithm without the artificial variable.
3. Do the table;
4. While the `Z` row contains negative values:
    1. Choose the pivot column: the most negative value in the `Z` row;
    2. Choose the pivot row: the line where (values column / pivot column) is the
    smallest positive value in the Z row;
    3. Change the base:

### Equation Method

- Slower than the graphical method (more verbose);
- More semantically clear than the table method;

## Branch and Bound

- Used to solve integer linear programming problems;
- Multiple simplex algorithms are used until we find a solution where all
  decision variables are integers.
- Multiple graphical methods can speed up the process: On the same graph, we
  draw the lines the problem's constraints, then we draw the lines each
  subproblem's constraints.
