# Article Exam Project

The goal of this project is to examine a MDWiki directory and make two lists:
1. Floating Articles: Existing markdown files which do not have a link pointing to them.
2. Missing Articles: Links inside the markdown which point to markdown files which do not yet exist.

I have chosen to complete this project in Python as it is a language which I would like more experience with. 

## Current Status

You can find [this project on GitHub](https://github.com/wPlachno/wp-article-examination)

The python file currently will either use the working directory or a directory passed in on the command line, find all the links in the markdown files, and output a list of "Floating Articles", or articles that do not have a link that points to them, followed by a list of "Missing Articles", or markdown files that should be made to match all existing links in other files. These lists are currently only being printed to the console.

### Future Tasks

1. Need to delete links

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

Note: This milestone was reached on 11/15/23

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

Note: This milestone was reached on 11/15/23

Now that we can open the files, we need to write a parser that finds all text between `")["` and the next `"]"`. Use regular expressions. 
```
The regular expression to use is 
\]\s?\([^\)]*\)
```

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

Note: This milestone was reached on 11/16/23

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

Note: This milestone was reached on 11/16/23

Make a function `linkMDFile` which takes two filenames, `parentName` and `childName`, and checks the dictionary for the `childName`. If it finds an existing `mdFile`, add `parentName` to the `parentLinks`. If the file does not exist, create a new `mdFile` with the filename, `last_modified = null`, no child links, and `parentName` as the only entry in the `parentLinks`. Add this `mdFile` to the dictionary. 

### 13. Apply links

Note: This milestone was reached on 11/16/23

For each `mdFile` in the dictionary, loop through `childLinks` and pass each through `linkMDFile` with the `mdFile.fileName` as the `parentLink`.

Expected output:
Same as step 11, but with non-zero NUM_LINKS and extra files.

### 14. Make and format output file

Note: This milestone was reached on 11/17/23

We can use Python's pickle library to serialize the ArticleExaminer after checking links. We can then deserialize the file after getting the directory path.

### 15. Use last_modified to reduce workload

Note: This milestone was reached on 11/18/23

By instantiating articles with a last_modified of 0, then checking if the last_modified on the file is larger (ie more seconds between modification and linux epoch), we can check only the files that have changes.

### 16. Check for removal of links

Note: This milestone was reached on 11/18/23

Now that we are only updating with changes, we need to reformat so that we can remove articles related to files that dont exist anymore.

### 17. Log large changes

Note: This milestone was reached on 11/18/23

Add log functionality to ArticleExaminer so we can track the addition and removal of both links and articles.

### 18. Support command line flag architectury and the VERBOSE flag

Note: This milestone was reached on 11/19/23

We can loop on all arguments, check for flags, and append directories. Make it easy to add a flag. The first should be VERBOSE, which should print any log entries that occur during the running of the script.

### 19. Implement DEBUG flag

Attention: This milestone needs to be tested

The DEBUG flag, on top of showing all debug messages, will also print a text-readable version of each of the articles.

### 20. Implement HISTORY flag

Attention: This milestone has not yet been reached

Triggering the history flag will print the entirety of the logs to the screen before running the rest of the script. If HISTORY is the only flag, the logs will be printed and the rest of the script will not run.

### 21. Implement ALLLINKS flag

Attention: this milestone has not yet been reached

ALLLINKS inserts a printing of all markdown links in each article just before the Floating and Missing list.

### 22. Implement NOCACHE flag

Attention: this milestone has not yet been reached

NOCACHE means that, if an aep-control.pickle file exists, it will not be opened, and, if the file does not exist, it will not be created.

### 23. Implement NONMD flag

Attention: This milestone has not yet been reached

When we print changes, we include added or removed links that point to images or URLs and other non-articles. If the ALLLINKS is also included, all links, including non-article links, will be printed. 