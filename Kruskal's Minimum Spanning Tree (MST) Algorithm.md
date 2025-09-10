# Ex. No: 18C - Kruskal's Minimum Spanning Tree (MST) Algorithm

## AIM:
To write a Python program for **Kruskal's algorithm** to find the Minimum Spanning Tree (MST) of a given connected, undirected, and weighted graph.

## ALGORITHM:

**Step 1**: Sort all the edges of the graph in non-decreasing order of their weights.

**Step 2**: Initialize the `parent[]` and `rank[]` arrays for each vertex to keep track of the disjoint sets.

**Step 3**: Iterate through the sorted edges and pick the smallest edge. Check whether including this edge will form a cycle using the union-find method:
- If the vertices of the edge belong to different sets, include it in the MST.
- Perform a union of these two sets.

**Step 4**: Repeat Step 3 until the MST contains exactly `V-1` edges.

**Step 5**: Print the edges included in the MST and the total minimum cost.

## PYTHON PROGRAM

```
from collections import defaultdict
class Graph:

	def __init__(self, vertices):
		self.V = vertices # No. of vertices
		self.graph = [] # default dictionary
		# to store graph


	def addEdge(self, u, v, w):
		self.graph.append([u, v, w])


	def find(self, parent, i):
		if parent[i] == i:
			return i
		return self.find(parent, parent[i])


	def union(self, parent, rank, x, y):
		xroot = self.find(parent, x)
		yroot = self.find(parent, y)


		if rank[xroot] < rank[yroot]:
			parent[xroot] = yroot
		elif rank[xroot] > rank[yroot]:
			parent[yroot] = xroot


		else:
			parent[yroot] = xroot
			rank[xroot] += 1

	def KruskalMST(self):

		result = [] # This will store the resultant MST
		

		i = 0
		
		e = 0

		self.graph = sorted(self.graph,
							key=lambda item: item[2])

		parent = []
		rank = []
		for node in range(self.V):
		    parent.append(node)
		    rank.append(0)
	
		while e < self.V - 1:

			# Step 2: Pick the smallest edge and increment
			# the index for next iteration
			u, v, w = self.graph[i]
			i = i + 1
			x = self.find(parent, u)
			y = self.find(parent, v)
       
			      
			if x != y:
				e = e + 1
				result.append([u, v, w])
				self.union(parent, rank, x, y)
		

		minimumCost = 0
		print ("Edges in the constructed MST")
		for u, v, weight in result:
			minimumCost += weight
			print("%d -- %d == %d" % (u, v, weight))
		print("Minimum Spanning Tree" , minimumCost)

g = Graph(4)
g.addEdge(0, 1, 10)
g.addEdge(0, 2, 6)
g.addEdge(0, 3, 5)
g.addEdge(1, 3, 15)
g.addEdge(2, 3, 4)

g.KruskalMST()
```

## OUTPUT
<img width="1035" height="348" alt="image" src="https://github.com/user-attachments/assets/06d8d798-bea2-4f18-b6c2-0ec1c93052b7" />


## RESULT
Thus the program for Kruskal's algorithm to find the Minimum Spanning Tree (MST) has been implemented and executed successfully.


