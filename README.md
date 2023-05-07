Download Link: https://assignmentchef.com/product/solved-meam620-project1-phase-2-3d-path-planning
<br>
Introduction

In this assignment you will begin building a trajectory generator for a quadrotor by implementing two graph search algorithms: Dijkstra’s algorithm and A*. The goal of this phase is to compute resolution optimal paths in a 3D environment from a start position to a goal position that avoids colliding with obstacles. This project is independent of Phase 1, but we will combine our planning and control algorithms in a subsequent phase.

Code Packet

Provided Files

<ul>

 <li>flightsim/world.py</li>

</ul>

The environments used for this assignment are defined by <strong><sub>World </sub></strong>objects. As documented in the file header, the world is defined by a dictionary containing the bounds of the world (’extents’), and a list of dictionaries of axis-aligned cuboid obstacles (’blocks’), which have ’extents’ and ’colors’. These worlds can be loaded from .json files like those provided in <sub>util/</sub>. We recommend you create more examples for yourself. Please do not submit or modify the World object code or any other files from <sub>flightsim/</sub>.

<ul>

 <li>code/occupancy_map.py</li>

</ul>

In order to find paths with a graph search algorithm in a <strong><sub>World</sub></strong>, it is necessary to first represent the environment as a graph. To do this we discretize space into a regular grid and attach graph nodes to each voxel. An <strong><sub>OccupancyMap </sub></strong>object is a voxel grid corresponding to a <strong><sub>World </sub></strong>object. Voxels with value <em><sub>False </sub></em>enclose free space while voxels with value <em><sub>True </sub></em>intersect obstacles.

The choice of grid resolution is especially important and impacts both the runtime of the algorithm as well as its ability to find a path. Another consideration is safety, which becomes critical when considering real world applications. Since quadrotors are not infinitesimal points but rather physical objects that take up space, it is important to ensure that generated paths avoid all obstacles in the environment with some margin. The appropriate choice of margin is a balance between safety and path length. Choose a margin too small and your quad may strike an obstacle and crash. Choose a margin too big and the goal may become inaccessible. The provided <strong><sub>OccupancyMap </sub></strong>class is already parameterized by the resolution of the discretization and the margin of inflation.

You are free to modify <sub>occupancy_map.py</sub>, though it is not necessary to complete the assignment.

<ul>

 <li>code/sandbox.py</li>

</ul>

This script loads a <sub>World</sub>, runs your algorithm, and plots the results. It is useful for debugging.

<ul>

 <li>util/test.py</li>

</ul>

This script runs tests against all <sub>test_*.json </sub>maps in <sub>util</sub>, including any you have created yourself.

Tasks

<ul>

 <li>graph_search.py</li>

</ul>

Your main task is to implement Dijkstra’s algorithm as described in class. A description of the inputs and expected outputs can be found in the header of the provided file.

A popular variant of Dijkstra’s algorithm is the A* algorithm. Since both algorithms are very similar, modify your completed graph search function so that when the astar parameter is <em><sub>True</sub></em>, it uses distance to the goal as a heuristic to guide the search. Remember that any heuristic must be admissible and consistent; if not, the algorithm is no longer guaranteed to return the shortest path.


