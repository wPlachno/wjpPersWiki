# MDWiki

MDWiki is a single file wiki solution that displays markdown files in the local directory. MDWiki does not have any editing capability, so the files must be created and modified using outside methods. This is a great solution for a publicly hosted knowledge base, but many may find the lack of editing capability a drawback.

The general workflow recommended for using MDWiki is to set it up on [Github Pages](github-pages.md), using Github's built-in hosting to view your personal wiki, while also tracking all changes in the repository. You can then use stackedit.io to edit the markdown files, though I personally use Notepad++ with the NPPMarkdownPanel plugin.

## Setting up MDWiki

[This tutorial](https://gist.github.com/0xdevalias/a8c3c2fd7bf2f50ff666) will walk you through hosting on Github Pages.

To setup MDWiki without the github portion, you just download and unzip [the release version](https://github.com/Dynalon/mdwiki/releases) and stick the mdwiki.html file into the folder that holds your index.html. 

At this point, you could open up your browser, http the server, and you will get something, but it will be almost completely empty. All you will see is an empty div followed by the MDWiki automatic site attribution. To add some introductory content, we can edit a config file and add a navigation bar.

MDWiki expects a config.json file in the same directory as the mdwiki.html file. If none exist, your server will be slowed down by 404s. Nonetheless, I suggest reading [here](http://dynalon.github.io/mdwiki/#!customizing.md) regarding what goes in the config file, as well as how to choose a color scheme. As an example, my config.json looks like:

	{
		"useSideMenu": true,
		"lineBreaks": "gfm",
		"additionalFooterText": "The Plachno Wiki, All content and images &copy; by William Plachno",
		"anchorCharacter": "#",
		"title": "Woodchipper Wiki"
	}

You can also set up your MDWiki with a navigation bar. This bar is defined by a navigation.md file in the same directory as the other files. You can read more about the navigation file [here](http://dynalon.github.io/mdwiki/#!quickstart.md) after the "Making a website out of it" header. My navigation.md is defined as follows: 

	[gimmick:theme](slate)
	
	# Woodchipper
	
	[Home](index.md)
	[About](about.md)
	
## Interesting MDWiki Things

[rbkhb's Natural Language Processing Class](https://github.com/auNLP/mdwikiNLP) is a Github hosted MDWiki built by a teacher to organize the materials for their class, including resources for each session and more.

[HaydenLeBaron's Wiki Visualizer](https://github.com/HaydenLeBaron/mdwiki-cartographer) is a python program that runs through a markdown library structured like MDWiki and generates a directed graph of the nodes and the links between them. So far, this is the closest thing to the visualization idea I had, but without the graphical prettyness.