# Markdown Cheat Sheet

This [Markdown cheat sheet](https://www.markdownguide.org/cheat-sheet/#downloads) was provided by [The Markdown Guide](https://www.markdownguide.org), with small edits by wPlachno.

This Markdown cheat sheet provides a quick overview of all the Markdown syntax elements. It can’t cover every edge case, so if you need more information about any of these elements, refer to the reference guides for [basic syntax](https://www.markdownguide.org/basic-syntax/) and [extended syntax](https://www.markdownguide.org/extended-syntax/).

## Basic Syntax

These are the elements outlined in John Gruber’s original design document. All Markdown applications support these elements.

### Heading

	# H1
	## H2
	### H3

# H1
## H2
### H3

### Bold

	**bold text**

**bold text**

### Italic

	*italicized text*

*italicized text*

### Blockquote

	> blockquote

> blockquote

### Ordered List

	1. First item
	2. Second item
	3. Third item

1. First item
2. Second item
3. Third item

### Unordered List

	- First item
	- Second item
	- Third item

- First item
- Second item
- Third item

### Code

	`code` 

`code`

### Inline Code

	We want `code` between this.

We want `code` between this.

### Horizontal Rule

	---

---

### Link

	[Markdown Guide](https://www.markdownguide.org)

[Markdown Guide](https://www.markdownguide.org)

### Image

	![alt text](https://www.markdownguide.org/assets/images/tux.png)

![alt text](https://www.markdownguide.org/assets/images/tux.png)

## Extended Syntax

These elements extend the basic syntax by adding additional features. Not all Markdown applications support these elements.

### Table

	| Syntax | Description |
	| ----------- | ----------- |
	| Header | Title |
	| Paragraph | Text |

| Syntax | Description |
| ----------- | ----------- |
| Header | Title |
| Paragraph | Text |

### Fenced Code Block

	```
	{
		"firstName": "John",
		"lastName": "Smith",
		"age": 25
	}
	```

```
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

### Footnote - NOT SUPPORTED IN MDWIKI

	Here's a sentence with a footnote. [^1]

	[^1]: This is the footnote.

Here's a sentence with a footnote. [^1]

[^1]: This is the footnote.

### Heading ID - NOT SUPPORTED IN MDWIKI

	### My Great Heading {#custom-id}

### My Great Heading {#custom-id}

### Definition List - NOT SUPPORTED IN MDWIKI

	term
	: definition

term
: definition

### Strikethrough

	~~The world is flat.~~

~~The world is flat.~~

### Task List - NOT SUPPORTED IN MDWIKI

	- [x] Write the press release
	- [ ] Update the website
	- [ ] Contact the media

- [x] Write the press release
- [ ] Update the website
- [ ] Contact the media

### Emoji - NOT SUPPORTED IN MDWIKI

	That is so funny! :joy:

That is so funny! :joy:

(See also [Copying and Pasting Emoji](https://www.markdownguide.org/extended-syntax/#copying-and-pasting-emoji))

### Highlight - NOT SUPPORTED IN MDWIKI

	I need to highlight these ==very important words==.

I need to highlight these ==very important words==.

### Subscript - NOT SUPPORTED IN MDWIKI

	H~2~O

H~2~O

### Superscript - NOT SUPPORTED IN MDWIKI

	X^2^

X^2^

### Mini Text

```
<sup>Mini Text</sup>
```

<sup>Mini Text</sup>