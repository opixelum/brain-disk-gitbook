# Graph Theory

## Vocabulary

- **Graph**: A graph is a set of vertices and edges;
- **Vertex**: Also called a node, it is a point in a graph;
- **Edge**: Also called an arc, it is a line between two vertices;
- **Path**: A sequence of vertices connected by edges;
- **Cycle**: A path that starts and ends at the same vertex;
- 
- **Loop**: An edge that connects a vertex to itself (a cycle of length 1);
- **Order**: The number of vertices in a graph;
- **Degree**: The number of edges connected to a vertex;
- **In-degree**: The number of edges pointing to a vertex;
- **Out-degree**: The number of edges pointing from a vertex.

## Types of Graphs

- **Undirected Graph**: A graph where the edges have no direction;
- **Directed Graph**: A graph where the edges have a direction;
- **Weighted Graph**: A graph where the edges have a weight;
- **Simple Graph**: A graph with no loops or multiple edges;
- **Complete Graph**: A graph where every vertex is connected to every other
  vertex;
- **Connected Graph**: A graph where there is a path between every pair of
  vertices.

## Paths

- **Simple Path**: A path where no vertex is repeated;
- **Elementary Path**: A path where no edge is repeated;
- **Hamiltonian Path**: A path that visits every vertex exactly once;
- **Eulerian Path**: A path that visits every edge exactly once;

## Algorithms

### Dijkstra

- Find the cheapest path between two nodes;
- Works on directed weighted graphs;

### A*

- A* = Dijkstra + heuristic;
- Heuristic = estimated distance to the goal;
- A* is optimal if the heuristic is admissible (never overestimates the distance
  to the goal);

#### Heuristics

- **Manhattan distance**: distance between two points measured along axes at
  right angles;

## Notes

- A table is a graph where:
  - The cells are vertices;
  - Going to a neighbor vertically or horizontally has a weight of 1;
  - Going to a neighbor diagonally has a weight of sqrt(2).
