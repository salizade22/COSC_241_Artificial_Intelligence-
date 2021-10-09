# Projects of the "Artificial Intelligence" course (CS 241, Amherst College)

This repository contains my solutions to the projects of the course 
of "Artificial Intelligence" (CS241) 

- [x] Project 1 - Search
- [x] Project 2 - Multi-agent Search
- [] Project 3 - MDPs and Reinforcement Learning 

##### Notes
- Each project is in its own folder. 

### Project 1 - Graph search - Implementation Notes
[Project 1](https://inst.eecs.berkeley.edu/~cs188/fa18/project1.html) is about applying 
graph search algorithms to PacMan (with no adversaries in the maze)

#### Question 1-4 - Search algorithms
All the search algorithms variants were implemented using a single 
generic search function and various `Fringe` implementations, one for each
search variant: 
- for DFS, it is stack 
- for BSF, it is queue 
- for UCS, it is a priority queue 
- for A*, it is a priority queue whose keys are computed summing 
the backward cost (as in UCS) to the estimated forward cost computed
by the provided heuristic.

States are wrapped in a `SearchNode` that stores: 

- the cost to reach the node,
- the previous node, 
- the action that led to the node. 

The path from the start node to a given node, as well as the 
corresponding action plan, is easily retrieved from the node itself 
by going backward to the start node.

Alternative implementations could:
- store the entire path in the node itself
- store the previous node in an external dictionary.

#### Question 6 - Eating foods on corners: heuristic
The heuristic was obtained by relaxation, assuming there are no walls in
the maze. It is obtained by summing:
1. the Manhattan distance to the nearest unvisited corner
2. the shortest Manhattan path from this corner to the remaining corners
(if any)

The second term is pre-computed for the cases in which the unvisited corners are 3 or 4, 
even though it wouldn't be expensive to compute.

#### Question 7 - Eating all dots: heuristic
The heuristic sums:
- the minimum cost for reaching any dot
- the maximum cost for going from the "nearest" dot found in the previous
step to another dot

The costs are obtained computing the optimal path to each single dot and
are cached in a dictionary to save computation.

In the auto-grading problem, the number of expanded nodes using the above heuristic (719) was way less than the maximum 
required for the maximum score (7000).

### Project 2 - Multi-Agent Search
[Project 2](https://inst.eecs.berkeley.edu/~cs188/fa18/project2.html) is about using 
MiniMax and ExpectiMax to implement a PacMan agent.

### Project 3 - MDPs and Reinforcement Learning
[Project 3](https://inst.eecs.berkeley.edu/~cs188/fa18/project3.html) is about developing 
a PacMan agent using reinforcement learning.
 
