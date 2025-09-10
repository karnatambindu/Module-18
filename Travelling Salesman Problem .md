# Ex. No: 18E - Travelling Salesman Problem (TSP)

## AIM:
To write a Python program to find the shortest possible route that visits every city exactly once and returns to the starting point using the **Travelling Salesman Problem (TSP)** approach.

## ALGORITHM:

**Step 1**: Start the program.

**Step 2**: Input the number of cities and the distance matrix.

**Step 3**: Set the starting city (e.g., city `0`).

**Step 4**: Generate all possible permutations of the remaining cities.

**Step 5**: For each permutation:
- Calculate the total cost of traveling through the permutation starting and ending at city `0`.
- Keep track of the **minimum cost** and the corresponding route.

**Step 6**: Return the **route** and the **minimum cost**.

**Step 7**: End the program.

## PYTHON PROGRAM

```
from sys import maxsize
from itertools import permutations
V = 4
def travellingSalesmanProblem(graph, s):


	vertex = []
	for i in range(V):
		if i != s:
			vertex.append(i)
	min_path=maxsize
	next_permutation=permutations(vertex)
	for i in next_permutation:
	    

	
		current_pathweight = 0
		k=s
		for j in i:
		    current_pathweight+=graph[k][j]
		    k=j
		current_pathweight+=graph[k][s]
		min_path=min(min_path, current_pathweight)
	return min_path

		
if __name__ == "__main__":


	graph = [[0, 10, 15, 20], [10, 0, 35, 25],
			[15, 35, 0, 30], [20, 25, 30, 0]]
	s = int(input())
	print(travellingSalesmanProblem(graph, s))
```

## OUTPUT
<img width="804" height="215" alt="image" src="https://github.com/user-attachments/assets/8093d6cf-08c2-4c1f-b871-3bbdb5c90c5d" />


## RESULT
Thus the program to find the shortest possible route using the Travelling Salesman Problem (TSP) approach has been implemented and executed successfully.

