# Article Exam Project

The goal of this project is to examine a MDWiki directory and make two lists:
1. Existing \*.md files which are not currently part of the main structure and do not have a link pointing to them.
2. Links inside the markdown which point to markdown files which do not yet exist.

I have chosen to complete this project in Python as it is a language which I would like more experience with. 

##  Milestones

### 1. Prepare development environment

Note: This milestone was reached on 11/12/23

It has been a while since I touched Python, so I'll need to reconfigure my environment.

Due to recommendations from family that are more familiar with Python, I chose to try out PyCharm. Installation was quick and the layout is excellently designed. 

### 2. Write "Hello World"

Note: This milestone was reached on 11/12/23

Once the environment is up, the next step is to do a sanity check: make sure you can run a python file.

Expected output:
```
> aep
...
Hello World!
```

### 3. Add 1 command line argument

Note: This milestone was reached on 11/13/23

Every language does this different. While I am sure I have done this before, I have no memory of how it was done.

Expected output:
```
> aep Gerald
...
Hello Gerald!
```

### 4. Check that the argument is a directory

Note: This milestone was reached on 11/13/23

Write a function `checkDirectory` which takes the argument and returns true if it is a url to a directory

Expected output:
```
> aep what-goes-up-must.md
...
what-goes-up-must.md is not a directory!
```
```
> aep what-goes-up-must/markdown/
...
what-goes-up-must/markdown/ is a directory
```

### 5. Get a list of the files in the directory

Note: This milestone was reached on 11/13/23

Write a function `exploreDirectory` which takes the argument and prints all files in the directory.

Expected output:
All files printed when given a directory as an argument.

### 6. Write a function to check if a filename points to a markdown file

Note: This milestone was reached on 11/14/23

Write a function `isMarkdown` which takes a filename and returns true if it ends in .md. 

Expected output:
All filenames printed when given a directory, each followed by a true/false of whether it is a markdown file.

### 7. Filter the directory list 

Note: This milestone was reached on 11/14/23

Write a function `exploreDirectory` which takes the argument and prints all files in the directory, as well as their `last_modified` date.

Expected output:
Prints all markdown filenames in the directory.

### 8. Print all markdown files.

Note: This milestone was reached on 11/14/23

For each markdown file in the directory, open the file and print it to the console.

Expected output:
Prints all markdown files in the directory.

### 9. Define structure

Attention: This milestone has not yet been reached.

We need an object, `mdFile`, for each markdown file which holds the `filename`, cut down to just the filename, not any upper directories, as well as the `last_modified` date of the file. The objects should also hold a list of child markdown links (`childLinks`), as well as a list of parent markdown links (`parentLinks`), initialized to empty, which will be crucial in the next couple steps. There should be a getter that counts the number of parents, and another for children. The object should be printable according to our expected output, with a check for `last_modified == null`, either printing LM or "Does not exist". All of these objects should be contained in a dictionary where the key is the filename.

Expected output:
```
!For each markdown file:
[FILE_NAME] ([NUM_PARENTS], [LAST_MODIFIED]/DNE):
- [LINKMD1]
...
- [LINKMDN]
Total: [NUM_CHILDREN]

```

### 10. Find all links in each file

Attention: This milestone has not yet been reached.

Now that we can open the files, we need to write a parser that finds all text between `")["` and the next `"]"`. Use regular expressions.

Expected output:
For each markdown file in the directory, it prints:
```
[FILE_NAME]:
- [LINK1]
- [LINK2]
...
- [LINKN]
```

### 11. Filter the link list 

Attention: This milestone has not yet been reached.

IF the link is a markdown file (use `isMarkdown`), add it to an array of links for that file.

Expected output:
For each markdown file in the directory, it prints:
```
[FILE_NAME]:
- [LINKMD1]
- [LINKMD2]
...
- [LINKMDN]
```

### 12. Make function for adding links

Attention: This milestone has not yet been reached.

Make a function `linkMDFile` which takes two filenames, `parentName` and `childName`, and checks the dictionary for the `childName`. If it finds an existing `mdFile`, add `parentName` to the `parentLinks`. If the file does not exist, create a new `mdFile` with the filename, `last_modified = null`, no child links, and `parentName` as the only entry in the `parentLinks`. Add this `mdFile` to the dictionary. 

### 13. Apply links

Attention: This milestone has not yet been reached.

For each `mdFile` in the dictionary, loop through `childLinks` and pass each through `linkMDFile` with the `mdFile.fileName` as the `parentLink`.

Expected output:
Same as step 11, but with non-zero NUM_LINKS and extra files.

### 14. Make and format output file

Attention: This milestone has not yet been reached