# Traveling Salesman Problem with Ant Colony Optimization
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

Funtion `goTo(A)`: Decides which city should the ant `A` go to. Its decision is based on the pheromones on each adjacent edge, and the formula below.
<p float="left">
  <img src="https://user-images.githubusercontent.com/12760574/130361954-666f4055-4937-41a4-86fe-c7a6bdfeee56.jpeg" width="400" />
</p>

Function `Move(A)`: Moves the ant `A`.

Function `Evaporate`: Evaporates the pheromones on the edges by the constant Evaporation Rate stored in `rEvap`.

### Output:
Outputs one integer: The length of the shortest cycle. And the sequence of the found cycle.

### Parameters:
Here I've provided the rolls of some parameter for finding the answer. Here, by "fitness", I meant "cost"; So the less it is, the better.

*Left:* The pheromone evaporation rate, *Center:* Number of ants, *Right:* Starting vertices of ants
<p float="left">
  <img src="https://user-images.githubusercontent.com/12760574/130435773-8fee6491-f7ba-4a9e-b350-a34ec51ba00e.png" width="300" />
  <img src="https://user-images.githubusercontent.com/12760574/130435940-548e2278-8c1d-4201-ad39-2e8c3f43c60f.png" width="300" />
  <img src="https://user-images.githubusercontent.com/12760574/130435986-0e900f5f-70e2-4d2c-8162-00e9d979d932.png" width="300" />
</p>

Although, these figures aren't very accurate as it's the result of running ant colony optimization on one particular testcase. Here's how changing the parameter alpha and beta (in the formula,) changes the result:
<p float="left">
  <img src="https://user-images.githubusercontent.com/12760574/130435773-8fee6491-f7ba-4a9e-b350-a34ec51ba00e.png" width="300" />
  <img src="https://user-images.githubusercontent.com/12760574/130435940-548e2278-8c1d-4201-ad39-2e8c3f43c60f.png" width="300" />
  <img src="https://user-images.githubusercontent.com/12760574/130435986-0e900f5f-70e2-4d2c-8162-00e9d979d932.png" width="300" />
</p>



#### Postlude:
The program reads the input from a file; The file `pr1002.tsp`, contains a sample input, consisting of 1002 vertices; I've downloaded this sample from [Heidelberg University' Site](http://comopt.ifi.uni-heidelberg.de/software/TSPLIB95/). The optimal answer for this testcase is `259045`.

This code, doesn't usually find the "best" solution, but it finds the near solutions very fast! Solving for `pr1002` with (only) genetic algorithm, needs a lot of time! a lot! But ant colony, found the answer `360761` in less than a min. The solution for this number is available in the notebook. 

For `bayg29.tsp`, the best answer is `1610`, this code doesn't usually finds this, but, it finds the solution about `1630` quite fast.
