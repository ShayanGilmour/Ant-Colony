# Traveling Salesman Problem with Ant-Colony
"Solving" the TSP via implementing Ant Colony Optimization with Python.

### Input:
The distances between each pair of vertices. There are two methods available in the code for reading the input. 
1.  At line `i`, there should be `n-i` space-separated integers; The `j`th integer indicates the distance between vertex `i` and `i+j`. 
2.  At line `i`, there should be three space-separated integers; First, the index of the vertex, second and third integers indicates the coordinate of the vertex.

### Process:
Using Ant Colony Optimization, it find the "shortest" cycle including every vertex.

There's a class called `Ant`:
  1. `visited`: The list of the cities with this ant has been there.
  1. `id`: The id of this ant
  1. `current`: The current city of the ant
  1. `fitness`: The sum of the distances this ant have traveled so far.

Funtion `goTo(A)`: Decides which city should the ant `A` go to. Its decision is based on the pheromones on each adjacent edge, and the formula below
<p float="left">
  <img src="https://user-images.githubusercontent.com/12760574/130361954-666f4055-4937-41a4-86fe-c7a6bdfeee56.jpeg" width="400" />
</p>

Function `Move(A)`: Moves the ant `A`.

Function `Evaporate`: Evaporates the pheromones on the edges by the constant Evaporation Rate stored in `rEvap`.

### Output:
Outputs one integer: The length of the shortest cycle. And the sequence of the found cycle.

#### Postlude:
The program reads the input from a file; The file `pr1002.tsp`, contains a sample input, consisting of 1002 vertices; I've downloaded this sample from [Heidelberg University' Site](http://comopt.ifi.uni-heidelberg.de/software/TSPLIB95/). The optimal answer for this testcase is `259045`.

This code, doesn't usually find the "best" solution, but it finds the near solutions very fast! Solving for `pr1002` with (only) genetic algorithm, needs a lot of time! a lot! But ant colony, found the answer `374272` in less than a min. The solution for this number is available in the notebook. 
