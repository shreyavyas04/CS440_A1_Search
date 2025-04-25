# score : 120/100

# Fast Trajectory Replanning: A* Search Variants

This repository contains our implementation for Assignment 1 in CS 440: Introduction to Artificial Intelligence (Fall 2024) at Rutgers University. The project focuses on trajectory planning using A* search algorithms in partially known grid environments. These environments simulate real-world navigation challenges faced in robotics and real-time strategy games.

## Team Members

- Shreya Vyas (218001583)  
- Ridhima Biswas (225004913)  
- Aditi Parekh (214002938)

## Project Summary

The objective of the project is to navigate an agent from a start cell to a target cell in a gridworld. The agent initially does not know which cells are blocked but can observe its four adjacent cells at each step. It uses this information to plan the shortest presumed-unblocked path to the target using variants of the A* algorithm.

We implemented and evaluated the following search strategies:

- Repeated Forward A* (RFA*)
- Repeated Backward A* (RBA*)
- Adaptive A* (AA*)

Each algorithm was tested on 50 randomly generated 101x101 gridworlds. The gridworlds were designed to simulate realistic obstacles and to require dynamic replanning as the agent discovers blocked cells.

## Concepts and Techniques

This project explores several core ideas from heuristic search:

- Use of Manhattan distance as a consistent and admissible heuristic for grid navigation
- Different tie-breaking strategies in A*, specifically comparing smaller versus larger g-values
- Comparison of forward and backward search directions
- Use of experience-based heuristic updates in Adaptive A* to reduce unnecessary exploration

## Experimental Findings

### Tie-Breaking in Repeated Forward A*

When comparing tie-breaking strategies:

- Favoring nodes with larger g-values resulted in fewer node expansions and improved runtime
- Favoring smaller g-values caused the algorithm to explore less promising paths, increasing the number of expanded nodes

This suggests that prioritizing nodes with more progress toward the goal (larger g-values) leads to more focused and efficient searches.

### Forward vs. Backward A* Search

We compared Repeated Forward A* and Repeated Backward A* in terms of performance:

- Repeated Forward A* expanded an average of 34,634 nodes
- Repeated Backward A* expanded slightly more nodes (37,186), but sometimes ran faster due to a more constrained search space near the goal

Overall, the effectiveness of forward versus backward search varied depending on the structure of the gridworld, particularly the density and location of obstacles.

### Adaptive A* Improvements

Adaptive A* significantly improved performance by reusing information from previous searches:

- It expanded fewer nodes (29,969) than Repeated Forward A*
- Its average runtime was significantly shorter (0.5841 seconds vs. 1.2925 seconds)

By updating heuristic values after each search, Adaptive A* directed future searches more efficiently and avoided redundant exploration.

## How to Run

To run any of the implemented algorithms:

1. Clone this repository
2. Navigate to the project directory
3. Run one of the scripts using a test gridworld:
   ```bash
   python src/repeated_forward.py --grid data/gridworlds/grid_01.txt
4. The script will output the agent's path and performance statistics, including node expansions and runtime

## Features

- Efficient use of a binary heap for managing the open list  
- Gridworlds generated using a randomized depth-first search for realistic pathfinding challenges  
- Visualization of agent paths for each algorithm  
- Mathematical proofs provided for heuristic admissibility and consistency in gridworlds  

## References

- Koenig, S., & Likhachev, M. (2005). *Adaptive A\**. Proceedings of the International Joint Conference on Autonomous Agents and Multiagent Systems (AAMAS), 1311–1312.  
- Cormen, T. H., Leiserson, C. E., Rivest, R. L., & Stein, C. (2001). *Introduction to Algorithms*. MIT Press.  

## Notes

This project was written using LaTeX for typesetting and submitted as a fully formatted PDF report. Additional credit was awarded for using LaTeX and for optionally implementing a custom binary heap from scratch.
