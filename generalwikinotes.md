# General Wiki Ideas

Please note that most of this article consists of my own theories and has not been peer-reviewed or even more than mildly scrutinized. These thoughts are more of a brainstorming session regarding my needs for [my own Content Management System](project_wiki.md).

## Types of Articles

Many wikis are used for many different reasons. This wiki was started as a personal knowledge base, meant to keep track of knowledge that the user does not want to lose. These knowledge articles usually come in three different varieties: 

1. **Subject Article**: These articles are what you are used to thinking of as a wiki article, some subject, covered to some level of completion, with links to other subjects. These can be relatively freeform, with the data flow being in a form that is distinct to the topic.

2. **Directory Article**: An article whose main purpose is to be a collection of links to another set of articles, as in [our home page](index.md). These links should also be arranged in a way that makes sense, and have a little bit more information that may include a quick summary, or the main points that make the article link worth being kept on the list.

3. **Journal Article**: While this type of article may revolve around a central subject or be mainly a list of links, the main *purpose* of the article is not related to the subject, but to the date it was written. These articles tend to be less important to make public, but should be searchable on request. 
 
With these three article types defined, there are some common structural ideas that generate naturally. 

- **Categorical Articles**: These are a set of  subject articles all centered around a topic, but with pages representing different variations. For these articles, a directory article is used as the central entry point, with links to each variation, and possibly some sort of central comparison table. The subject articles in this category should share some layout.

- **Notebooks**: A collection of journal articles written by the same person. In a wiki with no authorization, these are public and need to be organized by hand. If a wiki supports separate users, these notebooks can be private to the user who wrote them, or set to public. 

- **Personnel Articles**: A subject article about a specific person, which may include important data like their birthdate or, in a more secure wiki, their last known address. 

## Common Use Cases

While everyone has their own needs for using a personal wiki, there are some common use-cases. Whether a wiki is the best solution for these use cases is not discussed here, only that a wiki has been used this way. 

- **Contact List**: A list of personnel articles which usually include names, phone numbers, and birthdates, but may also include likes and dislikes, portraits, or even common conversation topics.

- **Code Repository**: With a wiki, any sort of code repository should be done in snippets. 

- **Inventory Management**: A description of a collection, either item by item or just a list. May include quantities, prices/values, and other important data. 

- **Journals**: Periodic entries whose purpose may include listing emotional state, a changelog of some sort, or even just trackers of whether or not a task was completed that day. 

- **Knowledge Base**: A collection of information for later retrieval. Unlike in a public wiki, where the knowledge is intended to be as complete as possible, the knowledge base of a personal wiki may be focused to only information that the user is likely to forget. 

- **Recipe Collection**: A set of articles used to store recipes, usually culinary recipes, which typically consist of a list of ingredients and a set of steps, but may also include a rating system, different sets of modifications, or a list of dates the recipe was used.

- **Walkthroughs**: A set of steps to accomplish a task. 

## Random Thoughts

### Link Shortcuts in Editor

A wiki editor should allow for saving the file right away, as well as having a markdown mode and a RTF mode. If using markdown, a cool feature would be to select some text and automatically convert it into a link, either using the web link in the clipboard ("Link From Clipboard"), or converting the text to [kebab-case](formattingcode.md) and instantiating an empty link ("Link to Markdown"). 

### Visualization Tool

As wikis fill with content, there are two cases that can be easy to miss or forget:

1. A link in markdown which does not resolve, usually because you knew it was something you wanted to have its own page, but either hadnt written it yet, or meant to double-check the correct spelling.
2. An article that has been written, but whose reference was never made or was deleted.

Both cases can be tracked with scripting pretty easily, so the question becomes "how should this be displayed?". We can easily just make a list of each case with a link on each list item to fix the problem, or we could have a visualization tool.

A visualization tool could be created to map the wiki in 3D space. [This has already been done](https://www.wikiverse.io/) for Wikipedia, with clustering of articles. This solution is cool, but much more of a hassle than necessary. There is also [this solution](https://wikioverdata.toolforge.org/wikitree/public/?q=Q1124&level=6&type=descendants&type_label=descendants&orientation=North&lang=en) which attempts to find a family tree by datamining Wikipedia.

#### Search Algorithm

If our wiki is structured with an index.md file, with links to articles with more links, then it can be described as a directed graph. 

First, we would need a tree. Each node of the tree represents an article and consists of the article name, and a list of nodes that it connects to, preferably  not alphabetical, but in order of contact. Ordering them this way means more important links, usually situated earlier in an article, could be expanded first.

Since cyclic links do exist, we need extra setup to disallow repeat nodes. We could use a String:Integer dictionary where the String is the name of the article, and the integer is whether the node has been expanded. If retrieval returns null, than the article has not yet been added to the tree. 

We also want a pointer to the current working node.