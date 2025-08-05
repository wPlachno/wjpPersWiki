

| Operator   | Method                       | Notes                                   |
| ---------- | ---------------------------- | --------------------------------------- |
| `+`        | `__add__(self, other)`       |                                         |
| `-`        | `__sub__(self, other)`       |                                         |
| `*`        | `__mul__(self, other)`       |                                         |
| `//`       | `__floordiv__(self, other)`  |                                         |
| `/`        | `__div__(self, other)`       |                                         |
| `/`        | `__truediv__(self, other)`   | when ``from __future__ import division` |
| `%`        | `__mod__(self, other)`       |                                         |
| `divmod()` | `__divmod__(self, other)`    |                                         |
| `**`       | `__pow__(self, other)`       |                                         |
| `<<`       | `__lshift__(self, other)`    |                                         |
| `>>`       | `__rshift__(self, other)`    |                                         |
| `&`        | `__and__(self, other)`       |                                         |
| `|`        | `__or__(self, other)`        |                                         |
| `^`        | `__xor__(self, other)`       |                                         |
| `+=`       | `__iadd__(self, other)`      |                                         |
| `-=`       | `__isub__(self, other)`      |                                         |
| `*=`       | `__imul__(self, other)`      |                                         |
| `//=`      | `__ifloordiv__(self, other)` |                                         |
| `/=`       | `__idiv__(self, other)`      |                                         |
| `/=`       | `__itruediv__(self, other)`  | when ``from __future__ import division` |
| `%=`       | `__imod__(self, other)`      |                                         |
| `**=`      | `__ipow__(self, other)`      |                                         |
| `<<=`      | `__ilshift__(self, other)`   |                                         |
| `>>=`      | `__irshift__(self, other)`   |                                         |
| `&=`       | `__iand__(self, other)`      |                                         |
| `|=`       | `__ior__(self, other)`       |                                         |
| `^=`       | `__ixor__(self, other)`      |                                         |