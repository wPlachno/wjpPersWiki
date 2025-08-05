#### Callable Classes

Defining `__call__(self, [args...])` allows your class to be called like a function, as in `my_object(arg1, arg2)`

#### Implementing `with`

The `with` keyword in Python allows for context management. At the beginning of the `with` statement, your objects `__enter__(self)` will be called, and the `__exit__(self, exception_type, exception value, traceback)` will be called when it exits, with all the non-`self` arguments None if successful. If an exception occurs, you can determine whether the exception gets passed to the owning code by returning `True` (if exception should be stopped) or `False` (if exception should be propagated).

#### [[Pickling Objects]]
![[Pickling Objects]]