---
title: Depth First Search
created: '2020-08-25T23:06:36.235Z'
modified: '2020-08-26T00:04:06.328Z'
---

# Depth First Search
- Explores nodes/edges depth first (follows one path to completion)
- Runs in **O(V + E)**

## Source Code
```python
n # number of nodes in the graph
g # adjacency list representing graph
visited = [False, ..., False] # size n

def dfs(at):
  if visited[at]: return
  visited[at] = True

  neighbours = g[at]
  for next in neighbours:
    dfs(next)

start_node = 0
dfs(start_node)
```

## Finding Connected Components
Start a DFS at every node (unless it is already visited) and mark all the reachable nodes as part of the same component. So, each group of connected nodes/components will have the same value

```python
n # number of nodes in the graph
g # adjacency list representing graph
visited = [False] * n
count = 0
components = [-1] * n

def findComponents():
  for i in range(n):
    if not visited[i]:
      count++
      dfs(i)
  return(count, components)

def dfs(at):
  visited[at] = True
  components[at] = count
  for next in g[at]:
    if not visited[next]:
      dfs(next)
```


