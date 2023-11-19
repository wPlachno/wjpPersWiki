# Python

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