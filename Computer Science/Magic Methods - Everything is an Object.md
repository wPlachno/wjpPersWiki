Magic Methods - Everything is an Object

In Python, all classes are objects. Thusly, there exist a set of methods that have special purposes, known as "Magic Methods". For more information, see [Rafe Kettler's A Guide To Python's Magic Methods](https://rszalski.github.io/magicmethods/#construction).

![[Life-Cycle Methods]]

![[Comparison Methods]]
![[Unary Operators]]
![[Arithmetic Operators]]

![[Type Conversion Methods]]
![[String Methods]]
### Container Methods

| Method                          | Usage                                                                                     |
| ------------------------------- | ----------------------------------------------------------------------------------------- |
| `__len__(self)`                 | `len(my_object)`                                                                          |
| `__getitem__(self, key)`        | `my_object[key]`                                                                          |
| `__setitem__(self, key, value)` | `my_object[key] = value`                                                                  |
| `__delitem__(self, key)`        | `del my_object[key]`                                                                      |
| `__iter__(self)`                | `iter(my_object)`, see [Iterators](https://www.w3schools.com/python/python_iterators.asp) |
| `__reversed__(self)`            | `reversed(my_object)`                                                                     |
| `__contains__(self, item)`      | Custom `in` check, returns `True` if found                                                |
| `__missing__(self, key)`        | What happens during `my_object[non_existant_key]`                                         |
|                                 |                                                                                           |

![[Other Methods]]