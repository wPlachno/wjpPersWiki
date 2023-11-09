# Article Exam Project

The goal of this project is to examine a MDWiki directory and make two lists:
1. Existing \*.md files which are not currently part of the main structure and do not have a link pointing to them.
2. Links inside the markdown which point to markdown files which do not yet exist.

I have chosen to complete this project in Python as it is a language which I would like more experience with. 

##  Milestones

### 1. Prepare development environment

Attention: This milestone has not yet been reached.

It has been a while since I touched Python, so I'll need to reconfigure my environment.

### 2. Write "Hello World"

Attention: This milestone has not yet been reached.

Once the environment is up, the next step is to do a sanity check: make sure you can run a python file.

Expected output:
```
> aep
...
Hello World!
```

### 3. Add 1 command line argument

Attention: This milestone has not yet been reached.

Every language does this different. While I am sure I have done this before, I have no memory of how it was done.

Expected output:
```
> aep Gerald
...
Hello Gerald!
```

### 4. Check that the argument is a markdown file

Attention: This milestone has not yet been reached.

Write a function checkMarkdown which takes a filename and outputs true if it ends in .md, and false if not. 

Expected output:
```
> aep what-goes-up-must.md
...
what-goes-up-must.md looks like a markdown file!
```
```
> aep what-goes-up-must.txt
...
Hello what-goes-up-must.txt!
```

### 5. Open and print the file

Attention: This milestone has not yet been reached.

Now that we can determine it is a markdown file, we need to be able to open it. Just print it.

Expected output: 
```
> aep gibberish-file.md
...
gibberish-file.md does not exist.
```
```
> aep project-article-exam.md
...
# Article Exam Project

The goal of this project is to examine a MDWiki directory and make two lists:
1. Existing \*.md files which are not currently part of the main structure and do not have a link pointing to them.
2. Links inside the markdown... (Rest of file still printed)
```

### 6. Print all links

Attention: This milestone has not yet been reached.

Write a function getLinks to parse the file and get a list of all the file's links. As a challenge to myself, I would like to do this with a Regular Expression. 

Expected output: 
```
> aep project-article-exam.md
...
No links exist in project-article-exam.md
```
```
> aep formatting-code.md
...
Found 1 link(s):
1. https://www.freecodecamp.org/news/snake-case-vs-camel-case-vs-pascal-case-vs-kebab-case-whats-the-difference/
```
```
> aep tailwind-css.md
...
Found 7 link(s):
1. https://webartisan.info/the-pros-and-cons-of-tailwindcss
2. https://tailwindcss.com/docs/hover-focus-and-other-states
3. https://tailwindcss.com/docs/installation/framework-guides
4. https://tailwindcss.com/docs/installation
5. https://tailwindcss.com/docs/installation/play-cdn
6. alpinejs.md
7. https://tailwindcss.com/docs/theme
```

### 7. Print only .md links

Attention: This milestone has not yet been reached.

Filter the list using the same function from Milestone 4.

Expected output: 
```
> aep project-article-exam.md
...
No links exist in project-article-exam.md
```
```
> aep formatting-code.md
...
No links exist in formatting-code.md
```
```
> aep tailwind-css.md
...
Found 1 link(s):
1. alpinejs.md
```

### 8. Make Tree Node class

Attention: This milestone has not yet been reached.

Make a Tree Node class which consists of a string `name`, a boolean `isExpanded`, a list `links`, and a list `nodes`. Write a function which, given a filename, creates a node, unexpanded, and finds all the markdown links. Write another function which prints the node. Instantiate one with the passed filename and print it.

Expected output: 
```
> aep project-article-exam.md
...
project-article-exam (Unexpanded): [], []
```
```
> aep formatting-code.md
...
formatting-code (Unexpanded): [], []
```
> aep tailwind-css.md
...
tailwind-css (Unexpanded): [alpinejs.md], []
```

### 9. Make Article Ledger class

Attention: This milestone has not yet been reached.

Make a class which handles a String:TreeNode dictionary, with instantiation, adding, and retrieval, as well as a list of Tree Nodes. Write a function which, given a Tree Node, adds it to the dictionary under its name. Create another function which takes a filename as an argument, calls the createTreeNode function, then the immediately previous function, and places the node into the list.

### 10. Write ArticleLedger.explore(fileNameArgument)

Attention: This milestone has not yet been reached.