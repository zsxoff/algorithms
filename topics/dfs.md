# DFS

## Теория

- [Поиск в глубину на канале YouTube - Олимпиадное программирование в УлГТУ](https://youtube.com/playlist?list=PLGhUJWLZ8uQ69hYB-AtVCerJ5yqh_5awR&feature=shared)

## Задачи

- [![LeetCode](https://img.shields.io/badge/LeetCode-00b8a3)](https://leetcode.com/problems/find-if-path-exists-in-graph) Find if Path Exists in Graph
- [![LeetCode](https://img.shields.io/badge/LeetCode-00b8a3)](https://leetcode.com/problems/island-perimeter) Island Perimeter
- [![LeetCode](https://img.shields.io/badge/LeetCode-00b8a3)](https://leetcode.com/problems/flood-fill) Flood Fill
- [![LeetCode](https://img.shields.io/badge/LeetCode-00b8a3)](https://leetcode.com/problems/number-of-islands) Number of Islands
- [![LeetCode](https://img.shields.io/badge/LeetCode-ff375f)](https://leetcode.com/problems/reconstruct-itinerary) Reconstruct Itinerary

## Алгоритмы

### Список смежности для представления графа

```python
graph = {
    0: set([1]),
    1: set([2, 3]),
    2: set([3]),
    3: set(),
    4: set(),
}
```

### Матрица смежности для представления графа

```python
graph = [
    [0, 1, 0, 0, 0],  # 0 --> {1}
    [0, 0, 1, 1, 0],  # 1 --> {2, 3}
    [0, 0, 0, 1, 0],  # 2 --> {3}
    [0, 0, 0, 0, 0],  # 3 --> {}
    [0, 0, 0, 0, 0],  # 4 --> {}
]
```

### DFS в графе для списка смежности

Сложность: `O(N + M)`, где `N` - число вершин, `M` - число ребер.

```python
def dfs(graph: dict[int, set[int]], v: int, visited: list[int]) -> None:
    visited[v] = 1

    for to in graph[v]:
        if not visited[to]:
            dfs(graph, to, visited)


def main():
    graph = {
        0: set([1]),
        1: set([2, 3]),
        2: set([3]),
        3: set(),
        4: set(),
    }

    visited = [0] * (len(graph))

    dfs(graph, 0, visited)

    print(visited)  # [1, 1, 1, 1, 0]
```

### DFS в графе для матрицы смежности

Сложность: `O(N^2)`, где `N` - число вершин.

```python
def dfs(graph: list[list[int]], v: int, visited: list[int]) -> None:
    visited[v] = 1

    for to in range(len(graph)):
        if graph[v][to] and not visited[to]:
            dfs(graph, to, visited)


def main():
    graph = [
        [0, 1, 0, 0, 0],  # 0 --> {1}
        [0, 0, 1, 1, 0],  # 1 --> {2, 3}
        [0, 0, 0, 1, 0],  # 2 --> {3}
        [0, 0, 0, 0, 0],  # 3 --> {}
        [0, 0, 0, 0, 0],  # 4 --> {}
    ]

    visited = [0] * len(graph)

    dfs(graph, 0, visited)

    print(visited)  # [1, 1, 1, 1, 0]
```
