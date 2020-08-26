---
title: Breadth First Search
created: '2020-08-25T23:54:00.949Z'
modified: '2020-08-26T00:20:27.759Z'
---

# Breadth First Search
- Explores nodes/edges in a graph breadth first (explores all neighbours first)
- Can find shortest path in an unweighted graph
- Runs in O(V + E)

## Source Code
Finding shortest path from two nodes in graph
```python
n # number of nodes in graph
g # adjacency list representing (unweighted) graph

# s = start node, e = end node, 0 <= e, s < n
def bfs(s, e):
  # Do a BFS starting at node s
  prev = solve(s)

  # Return reconstructed path from s -> e
  return reconstructPath(s, e, prev)

def solve(s):
  q = Queue()
  q.enqueue(s)

  visited = [False] * n
  visited[s] = True

  prev = [None] * n
  while not q.empty():
    node = q.dequeue()
    neighbours = g[node]
    
    for nex in neighbours:
      if not visited[nex]:
        q.enqueue(nex)
        visited[nex] = True
        prev[nex] = node
  return prev

def reconstructPath(s, e, prev):
  # Reconstruct path going backwards from e
  path = []
  at = e
  while (not at == None):
    path.append(at)
    at = prev[at]

  path.reverse()

  # If s and e are connected return the path
  if path[0] == s:
    return path
  return []
```
