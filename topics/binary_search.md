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
- [![LeetCode](https://img.shields.io/badge/LeetCode-ffc01e)](https://leetcode.com/problems/search-in-rotated-sorted-array) Search in Rotated Sorted Array
- [![LeetCode](https://img.shields.io/badge/LeetCode-ffc01e)](https://leetcode.com/problems/search-in-rotated-sorted-array-ii) Search in Rotated Sorted Array II
- [![LeetCode](https://img.shields.io/badge/LeetCode-ffc01e)](https://leetcode.com/problems/search-a-2d-matrix) Search a 2D Matrix
- [![LeetCode](https://img.shields.io/badge/LeetCode-ffc01e)](https://leetcode.com/problems/find-peak-element) Find Peak Element
- [![LeetCode](https://img.shields.io/badge/LeetCode-ffc01e)](https://leetcode.com/problems/find-a-peak-element-ii) Find Peak Element II
- [![LeetCode](https://img.shields.io/badge/LeetCode-ffc01e)](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array) Find Minimum in Rotated Sorted Array
- [![LeetCode](https://img.shields.io/badge/LeetCode-ff375f)](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array-ii) Find Minimum in Rotated Sorted Array II
- [![LeetCode](https://img.shields.io/badge/LeetCode-ffc01e)](https://leetcode.com/problems/search-a-2d-matrix-ii) Search a 2D Matrix II
- [![LeetCode](https://img.shields.io/badge/LeetCode-ffc01e)](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix) Kth Smallest Element in a Sorted Matrix
- [![LeetCode](https://img.shields.io/badge/LeetCode-ffc01e)](https://leetcode.com/problems/count-negative-numbers-in-a-sorted-matrix) Count Negative Numbers in a Sorted Matrix
- [![LeetCode](https://img.shields.io/badge/LeetCode-ffc01e)](https://leetcode.com/problems/longest-increasing-subsequence) Longest Increasing Subsequence
- [![LeetCode](https://img.shields.io/badge/LeetCode-ffc01e)](https://leetcode.com/problems/h-index-ii) H-Index II

## Алгоритмы

### Классический бинарный поиск

```python
def search(self, nums: list[int], target: int) -> int:
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

```text
Input: nums = [1, 3, 5, 6], target = 5
Output: 2
```

### Поиск левой границы элемента или отсутствия элемента

Алгоритм для отсортированного массива с повторениями:

```python
def binsearch_l(nums: list[int], target: int) -> int:
    l = 0
    r = len(nums) - 1

    while l <= r:
        m = (l + r) >> 1

        if nums[m] < target:
            l = m + 1
        elif nums[m] > target:
            r = m - 1
        else:
            # Проверка на достижение левой границы элемента
            if m == 0 or nums[m - 1] != nums[m]:
                return m
            else:
                r = m - 1

    return -1
```

```text
Input: nums = [0, 2, 2, 2, 3, 3, 3], target = 2
Output: 1
```

### Поиск правой границы элемента или отсутствия элемента

Алгоритм для отсортированного массива с повторениями:

```python
def binsearch_r(nums: list[int], target: int) -> int:
    l = 0
    r = len(nums) - 1

    while l <= r:
        m = (l + r) >> 1

        if nums[m] < target:
            l = m + 1
        elif nums[m] > target:
            r = m - 1
        else:
            # Проверка на достижение правой границы элемента
            if m == len(nums) - 1 or nums[m] != nums[m + 1]:
                return m
            else:
                l = m + 1

    return -1
```

```text
Input: nums = [0, 2, 2, 2, 3, 3, 3], target = 2
Output: 3
```
