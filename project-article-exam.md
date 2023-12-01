# Article Exam Project

The goal of this project is to examine a MDWiki directory and make two lists:
1. Floating Articles: Existing markdown files which do not have a link pointing to them.
2. Missing Articles: Links inside the markdown which point to markdown files which do not yet exist.

I have chosen to complete this project in Python as it is a language which I would like more experience with. 

## Current Status

You can find [this project on GitHub](https://github.com/wPlachno/wp-article-examination)

The python file currently will either use the working directory or a directory passed in on the command line, find all the links in the markdown files, and output a list of "Floating Articles", or articles that do not have a link that points to them, followed by a list of "Missing Articles", or markdown files that should be made to match all existing links in other files. These lists are currently only being printed to the console.

## Setup

This script was written with Python 3.10.5 in mind, so earlier versions have undefined reactions. Nonetheless, as long as you have that Python or later, the script should run. If you have an earlier version, go ahead and try it out. If you do, send me a message on github and I'll add it. 

## Usage

1. `py article-examination.py`
    If you run the script with no arguments, it will output the lists 
of floating articles and missing articles in the current working 
directory to the terminal. It will also create `aep-control.pickle`, the 
data file that represents the scripts cache.

2. `py article-examination.py wikis/wiki1 VERBOSE`
    This has 2 arguments - `wikis/wiki1`, a directory to run in, and 
`VERBOSE`, the first of our 4 command line flags.
    `VERBOSE` triggers the script to print any log messages to the 
console as they are triggered. This is different from the `HISTORY` flag, 
which does not run the main functionality of the script, and instead 
simply prints the entire log history to the terminal.

3. `py article-examination.py ALLLINKS wikis/wiki1 NOCACHE wikis/wiki2 NONMD DEBUG`
    This final example illustrates three things: that there is no 
required order between directories and flags, that you can have multiple 
directories and multiple files, and also shows the final supported flags. 
Please note that most flags can be combined except for `HISTORY`, which is 
designed to be called simply to check the log, not trigger the rest of 
the `ArticleExaminer` logic.
    `ALLLINKS` means to print a list of each of the links between articles, 
`NOCACHE` means to skip reading or writing `aep-control.pickle`, `NONMD` 
means to include non-article links, and `DEBUG` means to print all the 
debug messages and follow the script's main print with a print of 
all the `article` objects.
    What you should experience with this combination of arguments is 
that the script will first work on `wiki1`, printing out debug messages 
while checking the links, then printing out a list of each `article` 
and all of their links, including links to web urls and images, then 
printing the Floating Articles, then the Missing Articles, which will 
culminate in the final print of each of the `Article` objects. It will do 
all of this without opening or writing an `aep-control.pickle` file. 
    It will then repeat exactly that for `wiki2`. 

### Future Tasks

1. Excise classes to their own files.
2. Use PyTest for unit testing.

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

Note: This milestone was reached on 11/18/23

We can loop on all arguments, check for flags, and append directories. Make it easy to add a flag. The first should be VERBOSE, which should print any log entries that occur during the running of the script.

### 19. Implement DEBUG flag

Note: This milestone was reached on 11/19/23

The DEBUG flag, on top of showing all debug messages, will also print a text-readable version of each of the articles.

### 20. Implement HISTORY flag

Note: This milestone was reached on 11/19/23

Triggering the history flag will print the entirety of the logs to the screen before running the rest of the script. If HISTORY is the only flag, the logs will be printed and the rest of the script will not run.

### 21. Implement ALLLINKS flag

Note: This milestone was reached on 11/19/23

ALLLINKS inserts a printing of all markdown links in each article just before the Floating and Missing list.

### 22. Implement NOCACHE flag

Note: This milestone was reached on 11/19/23

NOCACHE means that, if an aep-control.pickle file exists, it will not be opened, and, if the file does not exist, it will not be created.

### 23. Implement NONMD flag

Note: This milestone was reached on 11/19/23

When we print changes, we include added or removed links that point to images or URLs and other non-articles. If the ALLLINKS is also included, all links, including non-article links, will be printed. 

### 24. Make all prints alphabetical

Note: This milestone was reached on 11/19/23

When we print, it should be standard to print our lists alphabetically, whether by the article name, or by the link.

### 25. Refactor for more modules

Note: This milestone was reached on 11/30/23

Move code to separate files, specifically, reduce article-examination.py to just the ArticleExaminer class, Article to article.py, and the main workflow to aep.py. Also, create the wcutil module for useful global code.

### 26. Add unit testing

Attention: This milestone has not yet been reached.

Yes, I know - this should have been milestone 2 or 3, but better late than never. As I will be using Pytest, this may end up taking longer. 

### 27. Implement PRINTART Flag

Attention: This milestone has not yet been reached. 

With this, we should update how we store the links. We should set up a link class, with the text of the link, the full line of text from the file, and the index of the link - `[file_name]_[line_number]`. The PRINTART flag should require one or more filenames after it, update the links, then output a detailed list of those links for the corresponding articles. 