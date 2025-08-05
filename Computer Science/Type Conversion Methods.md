
| Operator                  | Method                    | Notes                         |
| ------------------------- | ------------------------- | ----------------------------- |
| `int(my_object)`          | `__int__(self)`           |                               |
| `long(my_object)`         | `__long__(self)`          |                               |
| `float(my_object)`        | `__float__(self)`         |                               |
| `complex(my_object)`      | `__complex__(self)`       |                               |
| `oct(my_object)`          | `__oct__(self)`           |                               |
| `hex(my_object)`          | `__hex__(self)`           |                               |
| `collection[my_object]`   | `__index__(self)`         |                               |
| Conversion mid-arithmetic | `__coerce__(self, other)` | Returns (self, other) or None |