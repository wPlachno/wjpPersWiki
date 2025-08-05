
`pickle` is a built-in Python library for converting objects into a file to save state. While there are several magic methods involved, the two most common are `__getstate__(self)`, called by `pickle.dump(file, my_object)`, and `__setstate__(self, state)`, called by `my_object = pickle.load(file)`.

An example was provided in [Rafe Kettler's A Guide To Python's Magic Methods](https://rszalski.github.io/magicmethods/#construction).

``` Python
import time

class Slate:
    '''Class to store a string and a changelog, and forget its value when pickled.'''

    def __init__(self, value):
        self.value = value
        self.last_change = time.asctime()
        self.history = {}

    def change(self, new_value):
        # Change the value. Commit last value to history
        self.history[self.last_change] = self.value
        self.value = new_value
        self.last_change = time.asctime()

    def print_changes(self):
        print 'Changelog for Slate object:'
        for k, v in self.history.items():
            print '%s\t %s' % (k, v)

    def __getstate__(self):
        # Deliberately do not return self.value or self.last_change.
        # We want to have a "blank slate" when we unpickle.
        return self.history

    def __setstate__(self, state):
        # Make self.history = state and last_change and value undefined
        self.history = state
        self.value, self.last_change = None, None
```