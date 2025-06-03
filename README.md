# Search A Sorted 📚🔍

Welcome to the **Search A Sorted** repository! This project features a fast, non-interpolated searching algorithm designed for sorted lists. You can explore various search methods, including binary search, exponential search, and Fibonacci search. 

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Algorithms](#algorithms)
  - [Binary Search](#binary-search)
  - [Exponential Search](#exponential-search)
  - [Fibonacci Search](#fibonacci-search)
- [Contributing](#contributing)
- [License](#license)
- [Releases](#releases)

## Introduction

Searching through sorted lists is a common task in computer science. Efficient algorithms can significantly reduce the time it takes to find elements. This repository provides implementations of several searching algorithms that you can use in your projects.

## Features

- **Fast Searching**: Implementations of multiple algorithms for optimal performance.
- **Easy to Use**: Simple interface to integrate into your applications.
- **Well-Documented**: Clear explanations and examples for each algorithm.
- **Flexible**: Support for various data types and structures.

## Getting Started

To get started with the **Search A Sorted** project, clone the repository and install any required dependencies. 

```bash
git clone https://github.com/GRDRarda/search-a-sorted.git
cd search-a-sorted
```

### Prerequisites

Ensure you have the following installed:

- Python 3.x
- Git

## Usage

After cloning the repository, you can run the algorithms directly from the command line or integrate them into your applications. Here’s a simple example:

```python
from search import binary_search

sorted_list = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
result = binary_search(sorted_list, 5)

if result != -1:
    print("Element found at index:", result)
else:
    print("Element not found")
```

## Algorithms

### Binary Search

Binary search is a classic algorithm that divides the search interval in half. It works on sorted lists and has a time complexity of O(log n).

#### Implementation

Here’s a simple implementation of binary search:

```python
def binary_search(arr, target):
    left, right = 0, len(arr) - 1

    while left <= right:
        mid = left + (right - left) // 2

        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1

    return -1
```

### Exponential Search

Exponential search is useful for unbounded or infinite lists. It first finds a range where the target may reside and then performs a binary search within that range.

#### Implementation

```python
def exponential_search(arr, target):
    if arr[0] == target:
        return 0

    index = 1
    while index < len(arr) and arr[index] <= target:
        index *= 2

    return binary_search(arr[:min(index, len(arr))], target)
```

### Fibonacci Search

Fibonacci search uses Fibonacci numbers to find an element in a sorted array. It is efficient and works well for large datasets.

#### Implementation

```python
def fibonacci_search(arr, target):
    fib_m2 = 0
    fib_m1 = 1
    fib_m = fib_m2 + fib_m1

    while fib_m < len(arr):
        fib_m2 = fib_m1
        fib_m1 = fib_m
        fib_m = fib_m2 + fib_m1

    offset = -1

    while fib_m > 1:
        i = min(offset + fib_m2, len(arr) - 1)

        if arr[i] < target:
            fib_m = fib_m1
            fib_m1 = fib_m2
            fib_m2 = fib_m - fib_m1
            offset = i
        elif arr[i] > target:
            fib_m = fib_m2
            fib_m1 -= fib_m2
            fib_m2 = fib_m - fib_m1
        else:
            return i

    if fib_m1 and offset + 1 < len(arr) and arr[offset + 1] == target:
        return offset + 1

    return -1
```

## Contributing

We welcome contributions to enhance the **Search A Sorted** project. To contribute:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/YourFeature`).
3. Make your changes and commit them (`git commit -m 'Add new feature'`).
4. Push to the branch (`git push origin feature/YourFeature`).
5. Open a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Releases

For the latest releases, please visit our [Releases page](https://github.com/GRDRarda/search-a-sorted/releases). You can download the files and execute them as needed.

## Conclusion

Thank you for exploring the **Search A Sorted** repository. We hope you find these algorithms useful for your projects. If you have any questions or suggestions, feel free to reach out. Happy coding!