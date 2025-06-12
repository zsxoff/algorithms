# Очередь с приоритетом

## Задачи

Список задач с LeetCode:

- [LeetCode - Heap (Priority Queue)](https://leetcode.com/problem-list/heap-priority-queue/)

Отдельные задачи:

- [Last Stone Weight](https://leetcode.com/problems/last-stone-weight)
- [Maximum Product of Two Elements in an Array](https://leetcode.com/problems/maximum-product-of-two-elements-in-an-array)
- [Find Subsequence of Length K With the Largest Sum](https://leetcode.com/problems/find-subsequence-of-length-k-with-the-largest-sum)

## Теория

- [Описание очереди с приоритетом в документации Python](https://docs.python.org/3/library/heapq.html)

Кучи — это двоичные деревья, для которых каждый родительский узел имеет значение, меньшее или равное любому из его дочерних узлов.

Временная сложность:

| Операция    | Сложность                                                                              |
| :---------- | :------------------------------------------------------------------------------------- |
| heapify     | `O(n)`                                                                                 |
| heappush    | `O(log n)`                                                                             |
| heappop     | `O(log n)`                                                                             |
| heappushpop | `O(log n)`                                                                             |
| heapreplace | `O(log n)`                                                                             |
| merge       | `O(n log m)`, где `n` — количество элементов в куче, `m` — количество входных объектов |
| nlargest    | `O(n log k)`, где `n` — количество элементов в куче, `k` — аргумент функции            |
| nsmallest   | `O(n log k)`, где `n` — количество элементов в куче, `k` — аргумент функции            |

## Примеры реализации

- [Очередь с приоритетом на C в Python](https://github.com/python/cpython/blob/v3.13.0/Lib/heapq.py)

## Алгоритмы

Импорт модуля:

```python
import heapq
```

Функции модуля `heapq` работают **in-place**, то есть, перед началом работы, необходимо завести изменяемый список:

```python
>>> h = [2, 1, 3, 5, 4]
```

Превращение списка в очередь с приоритетом за линейное время:

```python
>>> heapq.heapify(h)
```

Получение `k` наибольших элементов за $$O(n log k)$$:

```python
>> heapq.nlargest(3, h)
[5, 4, 3]
```

Получение `k` наименьших элементов за $$O(n log k)$$:

```python
>> heapq.nsmallest(3, h)
[1, 2, 3]
```

Сохранение позиции элемента при использовании кучи (значение должно быть в начале):

```python
>>> h = [(x, i) for i, x in enumerate(nums)]
>>> heapify(h)
```

### Поиск подпоследовательностей с максимальной или минимальной суммой

Алгоритм эффективен при $$k << n$$, где $$n$$ — размер списка, $$k$$ — размер подпоследовательности.

Временная сложность алгоритма: $$O(n) + O(n logk) + O(k logk)$$, что при достаточно малых $$k$$ может стремиться к $$O(n)$$.

Тем не менее, алгоритм может быть менее эффективен, чем алгоритм скользящего окна со сложностью $$O(n)$$.

```python
from heapq import heapify, nsmallest, nlargest

nums = [1, 5, 7, 3, 2]

h = [(x, i) for i, x in enumerate(nums)]
heapify(h)

k = 3

# Подпоследовательность с максимальной суммой
subsequence_max = [x[0] for x in nsmallest(k, nlargest(k, h), key=lambda x: x[1])]
subsequence_max  # [5, 7, 3]

# Подпоследовательность с минимальной суммой
subsequence_min = [x[0] for x in nsmallest(k, nsmallest(k, h), key=lambda x: x[1])]
subsequence_min  # [1, 3, 2]
```
