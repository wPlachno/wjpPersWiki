
| Operator       | Method                 | Notes                     |
| -------------- | ---------------------- | ------------------------- |
| `==`           | `__eq__(self, other)`  |                           |
| `!=`           | `__ne__(self, other)`  |                           |
| `<`            | `__lt__(self, other)`  |                           |
| `>`            | `__gt__(self, other)`  |                           |
| `<=`           | `__le__(self, other)`  |                           |
| `>=`           | `__ge__(self, other)`  |                           |
| `<`, `==`, `>` | `__cmp__(self, other)` | <0: `<`; 0: `==`; >0: `>` |