
| Operator                | Method               | Notes                             |
| ----------------------- | -------------------- | --------------------------------- |
| `+my_object`            | `__pos__(self)`      |                                   |
| `-my_object`            | `__neg__(self)`      |                                   |
| `abs(my_object)`        | `__abs__(self)`      |                                   |
| `~my_object`            | `__invert__(self)`   |                                   |
| `round(self, n)`        | `__round__(self, n)` | `n` = decimal places to round to. |
| `math.floor(my_object)` | `__floor__(self)`    |                                   |
| `math.ceil(my_object)`  | `__ceil__(self)`     |                                   |
| `math.trunc(my_object)` | `__trunc__(self)`    |                                   |