# arachnea

arachnea is a Python library that allows you to perform efficient array operations using a fluent API approach inspired by the agility and efficiency of spiders.

## Features

- **Map**: Transform each element of an array using a provided function.
- **Filter**: Filter elements of an array based on a provided condition.
- **Reduce**: Reduce an array to a single value based on a provided accumulator and transformation function.
- **Find**: Find the first element in the array that meets the given condition.
- **Remove**: Remove the first element in the array that meets the given condition.
- **ForEach**: Execute a provided function once for each array element.

## Installation

You can install arachnea via pip:

```bash
pip install arachnea
```

## Usage

### Basic Usage

```python
from arachnea import arachnea

numbers = [1, 2, 3, 4, 5]

arachnea(numbers).for_each(lambda num: print(num * 2))  # Example of using forEach
```

### API Examples

#### Mapping and Reducing

```python
numbers = [1, 2, 3, 4, 5]

sum_of_squares = (
    arachnea(numbers)
    .map(lambda num: num * num)
    .reduce(lambda acc, num: acc + num, 0)
)

print(sum_of_squares)  # Output: 55
```

#### Filtering and Collecting

```python
numbers = [1, 2, 3, 4, 5]

odd_numbers = (
    arachnea(numbers)
    .filter(lambda num: num % 2 != 0)
    .collect()
)

print(odd_numbers)  # Output: [1, 3, 5]
```

#### Removing Elements

```python
numbers = [1, 2, 3, 4, 5]

remove_4 = (
    arachnea(numbers)
    .map(lambda num: num * num)
    .remove(4)
    .collect()
)

print(remove_4)  # Output: [1, 9, 16, 25]
```

#### Finding Elements

```python
numbers = [1, 2, 3, 4, 5]

greater_than_twenty_four = (
    arachnea(numbers)
    .map(lambda num: num * num)
    .find(lambda num: num > 24)
)

print(greater_than_twenty_four)  # Output: 25
```

#### Chaining Operations

```python
numbers = [1, 2, 3, 4, 5]

result = (
    arachnea(numbers)
    .filter(lambda num: num > 2)
    .map(lambda num: num * 3)
    .reduce(lambda acc, num: acc + num, 0)
)

print(result)  # Output: 39
```

## API

### `map(transformer: (element: T) => K) -> Stream[K]`

Transforms each element of the array using the provided transformer function.

### `filter(condition: (element: T) => bool) -> Stream[T]`

Filters elements of the array based on the provided boolean condition function.

### `reduce(reducer: (accumulator: K, element: T) => K, initial_value: K) -> K`

Reduces the array to a single value using the provided reducer function and initial value.

### `remove(condition: (element: T) => bool | T) -> Stream[T]`

Removes the first element in the array that meets the given condition or is equal to the given parameter.

### `find(condition: (element: T) => bool | T) -> T`

Finds the first element in the array that meets the given condition or is equal to the given parameter.

### `for_each(action: (element: T) => None) -> None`

Executes a provided function once for each array element.

### `collect() -> List[T]`

Collects the elements after applying all transformations and filters, returning them as a list.

## Todo

- Combine successive filter operations into a single operation.
- Document `actionsLoop` for custom terminating operation injection.
- Improve the performance of atomic operations.
- Add sorting, flattening functionality.
- Enhance performance optimizations.
- Implement error handling for edge cases.

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request.