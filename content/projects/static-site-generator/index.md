# Markdown Static Site Generator

[< Back Home](/)

I built a lightweight markdown parsing pipeline that can generate static websites, which I host on GitHub. 

I wanted to build a pipeline that handles transformation of data across multiple stages.  My favourite part was figuring out how to take a messy input format and break it down into smaller, manageable stages, and giving each stage a single clear responsibility.

The project takes markdown (.md) files, parses their structure and formatting, converts them into HTML, and then produces the static pages used to build a website.

In fact, _this project is powering the site you're looking at right now._

You can [view the live project](https://tmcausla.github.io/Static-site-generator/).

You can also [view the source on GitHub](https://github.com/tmcausla/Static-site-generator) and try it out yourself!

## Tech Stack

- Python (with unittest library)
- Linux
- Git / GitHub
- HTML
- CSS

## How It Works

The pipeline breaks Markdown processing into several stages rather than trying to convert everything in one pass.  

The Markdown is first divided into blocks such as headings, paragraphs, quotes, lists, and code blocks.  These blocks are then parsed for inline formatting for features such as **bold**, _italics_, links, and images.

The resulting data is represented using TextNode and HTML Node objects before being rendered as HTML.  This separation makes the individual stages easier to test, debug, and build on.  

The content is written out in markdown files like this:

```
**Bold text** looks like this.
Italics are made with _underscores_.
> It can parse quotes
> across multiple lines
> - Linus Torvalds, probably
## The Good
- Easy to create
- Easy to read
- Easy to grow
- No database required
## The Bad
1. Not nearly as robust compared against modern website framework
2. Interactive functionality isn't really a thing
3. Have fun hunting down that one syntax/spelling error
### The Ugly
The manual parsing pipeline.
Markdown is simple and straightforward until you ask things like:
"_What happens if someone puts a list inside a blockquote containing italic text with a link?_"
At that point, just start writing regex and questioning your life choices.
```

The HTML created by this file is featured below.

## The Pipeline

```
Markdown file
    |
    v
Blocks of text
    |
    v
Inline parsing
    |
    v
TextNodes
    |
    v
HTML Nodes
    |
    v
Static HTML
```

## Now Let's See It For Real

**Bold text** looks like this.

Italics are made with _underscores_.

> It can parse quotes
> across multiple lines
> - Linus Torvalds, probably

## The Good

- Easy to create
- Easy to read
- Easy to grow
- No database required

## The Bad

1. Not nearly as robust compared against modern web frameworks
2. Interactive functionality isn't really a thing
3. Have fun hunting down that one syntax/spelling error

### The Ugly

The manual parsing pipeline.

Markdown is simple and straightforward until you ask things like:

"_What happens if someone puts a list inside a blockquote containing italic text with a link?_"

At that point, just start writing regex and questioning your life choices.

[< Back Home](/)
