# Бинарный поиск

## Теория

- [Описание алгоритма на сайте Algorithms for Competitive Programming](https://cp-algorithms.com/num_methods/binary_search.html)

## Примеры реализации

- [Бинарный поиск на C в Python](https://github.com/python/cpython/blob/main/Modules/_bisectmodule.c)
- [Оптимизация бинарного поиска для Rust](https://rustmagazine.org/issue-2/optimize-binary-search/)

## Задачи

- [![LeetCode](https://img.shields.io/badge/LeetCode-00b8a3)](https://leetcode.com/problems/search-insert-position) Search Insert Position
- [![LeetCode](https://img.shields.io/badge/LeetCode-00b8a3)](https://leetcode.com/problems/binary-search) Binary Search
- [![LeetCode](https://img.shields.io/badge/LeetCode-ffc01e)](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array) Find First and Last Position of Element in Sorted Array

## Алгоритмы

### Классический бинарный поиск

```python
def search(self, nums: List[int], target: int) -> int:
    l = 0
    r = len(nums) - 1

    while l <= r:
        m = (l + r) >> 1

        if nums[m] < target:
            l = m + 1
        elif nums[m] > target:
            r = m - 1
        else:
            return m

    return -1
```

### Поиск левой границы элемента или отсутствия элемента

```python
def binsearch_l(nums: List[int], target: int) -> int:
    l = 0
    r = len(nums) - 1

    while l <= r:
        m = (l + r) >> 1

        if nums[m] < target:
            l = m + 1
        elif nums[m] > target:
            r = m - 1
        else:
            # Проверка на достижение левой границы
            if m == 0 or nums[m - 1] != nums[m]:
                return m
            else:
                r = m - 1

    return -1
```

### Поиск правой границы элемента или отсутствия элемента

```python
def binsearch_r(nums: List[int], target: int) -> int:
    l = 0
    r = len(nums) - 1

    while l <= r:
        m = (l + r) >> 1

        if nums[m] < target:
            l = m + 1
        elif nums[m] > target:
            r = m - 1
        else:
            # Проверка на достижение правой границы
            if m == len(nums) - 1 or nums[m] != nums[m + 1]:
                return m
            else:
                l = m + 1

    return -1
```
