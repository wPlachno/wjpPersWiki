
| Method                            | Purpose                               |
| --------------------------------- | ------------------------------------- |
| `__str__(self)`                   | Human readable for `str(my_object)`   |
| `__repr__(self)`                  | Machine readable.                     |
| `__unicode__(self)`               | `str()` but with unicode.             |
| `__format__(self, format_string)` | `string.format("{my_object}")`        |
| `__hash__(self)`                  | `hash(my_object)`                     |
| `__nonzero__(self)`               | `bool(my_object)`                     |
| `__dir__(self)`                   | `dir(my_object)` should list all attr |
| `__sizeof__(self)`                | The size in bytes, `sys.getsizeof()`                                      |