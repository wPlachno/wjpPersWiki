# Python

## Documentation

You should use triple quotes after a function definition to include for a pydoc. 
``` Python
    def get_non_md_links(self):
        """
        Compares the articles all_links list with its md_links list and
        returns the difference
        :return: The links which exist in all_links, but not in md_links
        """
        non_md_links = []
        for link in self.all_links:
            if link not in self.md_links:
                non_md_links.append(link)
        return non_md_links
```

## Logical Fixtures

Python has many of the common logical fixtures: `if-elif-else`, `for x in sample_list`, `while x`, and more. In loops, you can use `break` to cancel out of the fixture, or `continue` to end the current loop and begin the next. You can also use `else` with the loops to notate code to run as soon as the loops conditional flips. This `else` block will not be triggered if `break` is used. Empty logical fixtures should contain the keyword `pass`. 

### Fixture Shorthands

The `if` and `for` fixtures have shorthands, or ternary operators.

#### If Shorthand

The if shorthand is built for quick single call conditionals. All on the same line, you write the code to execute if true, `if`, then the conditional. You could optionally continue with `else` then the code to run when the conditional is true.

``` Python
is_even = x%2 == 0
print("x is even!") if is_even else print("x is odd!")
```

#### For Shorthand

The for shorthand does a single call for a range. All in square brackets, write the repeating line of code, then the for statement.

``` Python
[print(item.name) for item in my_list]
```

### Range

The `range` function is built-in and generates a list of numbers. If the only argument is a number, it will return a list of numbers from 0 to that number, exclusive (0 -> n-1), but you can also pass two numbers and generate a list from x to y. A third parameter will set the step number. `range(3,24,3)` will return the list `[3,6,9,12,15,18,21]`.   

## Data Collections

Python supports the data collections known as tuples, lists, sets, and dictionaries. A tuple is a collection that is ordered and unchangeable, lists are ordered, changeable, and allow duplicates, sets are unordered, unchangeable (but still add/removeable), and unindexed, while dictionaries are ordered, changeable, and do not allow duplicates.

| Collection   | Ordered | Changeable | Duplicates |
| ------------ | ------- | ---------- | ---------- |
| Tuples       | True    | False      | True       |
| Lists        | True    | True       | True       |
| Sets         | False   | False-ish  | False      |
| Dictionaries | True    | True       | False      |

### Collection Methods

Many collections share common methods.

| Collection   | Construction    | Access    | Modification | Removal        | Copy         |
| ------------ | --------------- | --------- | ------------ | -------------- | ------------ |
| Tuples | tuple((a,b,c)), =(val,) | t[i] | Cast to List | Cast to List | t.copy() |
| Lists | list(), = [x,y] | list[i] | list[i]=x | list.remove(x) | list.copy(y) |
| Sets | set((a,b,c)), = {a,b,c} | in set | set.add(x) | set.remove(x) | set.copy(y) |
| Dictionaries | dict(), = [x:a,y:b] | dict[key] | dict[key]=x | del dict[key] | dict.copy() | 

### Tuples

A tuple is an ordered unchangeable collection of items. To do any modification, you can cast it to a list using the `list()` constructor, make the edits, then recast using the `tuple()` constructor. 

#### Unpacking Tuples

You can unpack a tuple into variables. If the number of variables you are unpacking to is less than the number of elements in the tuple, you can add an asterix before a variable for the variable to be a list of a size adequate to balance the variables to tuple elements. From the [w3schools article on unpacking](https://www.w3schools.com/python/python_tuples_unpack.asp):

``` Python
fruits = ("apple", "banana", "cherry", "strawberry", "raspberry")

(green, yellow, *red) = fruits

print(green)
print(yellow)
print(red)
--------------------
Output:
apple
banana
['cherry', 'strawberry', 'raspberry']
```

### Lists

Lists are pythons equivalent of arrays. Instantiation can be triggered using the `list()` constructor or just setting `sample_list = ()`. You can access or modify values using the index operator, `sample_list[1]`. You can insert an item at a certain index using the `sample_list.insert(item_index, item_value)`, or find an items index using the `index(val)` method. You can add an item at the end of the list using the `append` method for a single item, or a full list using either the `extend` method or the `+` operator. The `pop` method can remove the final element, but the `remove` method or the `del` keyword will both excise a given value. You can find how many times a value appears in the list using the `count` method, or reset a list using the `clear` method.

#### List Subsets

A subset can be accessed using `sample_list[inclusive_start_index:exclusive_end_index`. These indexes may be negative to reference indexes from the end of the list. For example, `sample_list[-4:-2]` will return a list of the elements at `n-4` and `n-3`. 

You can also use subsets with the assignment operator. If you use `sample_list[1:2]=[item_4]`, the item at index 1 will be set to `item_4`. Note that `item_4` is enclosed in a list. You can do this same process, but use a list on the right side of the operator that has a different length than the subrange you are assigning to. If you assign an extra item, it will insert the extra item between the final element of the subrange and the first element not included. If you assign less items, the entire list collapses down as expected. 

#### List Comprehension 

When dealing with lists, you can compose new lists with list comprehension. For a more in-depth understanding, see [the w3schools article on List Comprehension](https://www.w3schools.com/python/python_lists_comprehension.asp), but the general syntax (quoted from the same article) is

#### Sorting Lists

Lists come with a default `sort()` method that sorts the items based on their `>` condition. The sort method allows for several arguments, including `key`, a function `function_name(n): return integer` to use for the sort, with the return integer ordering items. Other arguments include `reverse`, which flips the direction of the list, though lists do have a built-in `reverse` method.

``` Python
newlist = [expression for item in iterable if condition == True]
```

### Sets

Sets are a collection similar to Lists, but are unordered, unchangeable and do not allow duplicates. With the duplicate restriction in mind, it is good to know that sets consider True and 1 the same value, as well as False and 0. You can instantiate a set using `sample_set = {a,b,c}` or `sample_set = set((a,b,c))`. You cannot access individual items in the set specifically, but you can check to see `if x in set` or loop through the set with `for x in sample_set`. There are two ways to remove a value from the set: `sample_set.remove(x)` or `sample_set.discard(x)`. The difference between the two is how they handle not finding the item in the set. The `remove` method will raise an exception, but the `discard` will fail gracefully. You can use a `pop` method to remove an item, but it will remove a random item from the set. To reset a set, you can call the `clear` method, or delete it with `del sample_set`. 

You can add a new item using the `add` method, or add a full set (or any other collection) with `update`. Note that `update` adds the items from the collection to your set, or you can use `sample_set.union(other_set)` to create a brand new set containing all items, with no duplicates. If you are interested in only the items in both sets, you can use the `sample_set.intersection_update(other_set)` to modify your set or `sample_set.intersection(other_set)` to return a new set. The same idea applies to the `symmetric_difference_update()` and `symmetric_difference()` methods, which find only the items not existing in both. There are also comparison functions between sets: `isdisjoint`, whether an intersection exists, `issubset`, whether this set is contained in another, and `issuperset`, whether this set contains the other.

### Dictionaries

Ddictionaries allow you to hold some data corresponding to a label, more commonly referred to as a key-value pair. Initializing a variable to square brackets makes it a dictionary. You can access or modify a value by supplying the key in square brackets after the name, though you can also modify a value by using the update method. Removing a value can be done using the `pop` method or using `del sample_dictionary["item_key"]`. You can also delete the dictionary using `del` or clear it using the `clear` method. You can find how many values exist in a dictionary by calling the `len` function, but looping through the dictionary is built into the `for x in sample_dictionary` formula, and you can do so even for the `sample_dictionary.keys` or `sample_dictionary.values`, or both as `for x, y in sample_dictionary.items()`. Using the assignment operator simply uses a reference, so if you want to make a copy, you should use `sample_dictionary.copy()` method or pass the source dictionary into the `dict()` constructor.  

## Common Imports

In Python, you need to import libraries you need. You do so by sticking a line near the top of the script saying `import LIBRARY_NAME`. 

**sys**: You can use sys.argv[] to check command line arguments.

**Variable Declaration**:
``` Python

```
**Print to User**: `print ("Text")`
**Input from User**: `input ("Please enter text: ")`
**Comments**: ` # Comment `
**If**:
``` Python
if a == b:
	# a = b
elif a < b:
	# a < b
else:
	# a > b 
# Afterwards...
```
**While**:
``` Python
while a < b:
	# loopy
else: 
	# once loop ends
# After else
```
**For**:
``` Python
for i in range(1,5,2): 
	# i = [1,3], range(i^0=1, i<5, i=i+2)
else:
	# Immediately after loop
```
For more information on the more basic pieces of the Python language, [click here](https://python.swaroopch.com/basics.html).

## Finding the filepath
According to [Stack Overflow](https://stackoverflow.com/questions/3430372/how-do-i-get-the-full-path-of-the-current-files-directory), `__file__` is the filepath of the current running Python script. 

For the directory of the script being run:
```
import pathlib
pathlib.Path(__file__).parent.resolve()
```
For the current working directory:
```
import pathlib
pathlib.Path().resolve()
```

## Serialization

Python has a built in library, called Pickle, for serialization of classes. 

``` Python
import pickle
...
Serialization:
...
	with open(control_path, "wb") as control_file:
		pickle.dump(self, control_file)
...
Deserialization:
...
	with open(control_path, "rb") as control_file:
		new_article_examiner = pickle.load(control_file)
	return new_article_examiner
```
Note that pickle will not work if you do not include the 'b' in the access rights. 

## Popular IDEs

PyCharm
Visual Studio Code

## Interesting Links

[A Byte of Python](https://python.swaroopch.com/) is a free internet book that serves as an introduction to Python. 

[GraphViz](https://www.graphviz.org/) is an open-source graphing solution I originally found in [HaydenLeBaron's Wiki Visualizer](https://github.com/HaydenLeBaron/mdwiki-cartographer). It seems to be more portable than I originally thought. I want to get more comfortable using this. The python library [graphviz](https://graphviz.readthedocs.io/en/stable/manual.html) implements the larger library in this language.