# Markdown
Markdown is a lightweight *markup language* that you can use to add formatting elements to plaintext text documents. When you create a Markdown-formatted file, you add Markdown syntax to the text to indicate which words and phrases should look different. It is a fast and easy way to take notes, create content for a website, and produce print-ready documents.

When you write in Markdown, the text is stored in a plaintext file that has an *.md* or *.markdown* extension. You need a Markdown application capable of processing the Markdown file. These applications convert Markdown-formatted text to HTML so it can be displayed in web browsers. Markdown applications use something called a Markdown processor (also commonly referred to as a “parser” or an “implementation”) to take the Markdown-formatted text and output it to HTML format. At that point, your document can be viewed in a web browser or combined with a style sheet and printed.

## Basic Syntax
### Headings
\# Heading level 1  -> \<h1>Heading level 1\</h1><br>
2,3,4,5<br>
\###### Heading level 6 ->\<h6>Heading level 6\</h1><br>
For headings with id, use ===== (to create h1) or ------- ( to create h2) under that line.<br>

### Paragraphs
To create paragraphs, use a blank line to separate one or more lines of text.<br>
Don't put tabs or spaces in front of your paragraphs. Keep lines left-aligned.<br>
\<p>just like this in HTML\</p>

### Line Breaks
To create a line break or new line (\<br>), end a line with two or more spaces, and then type return.  
Or you can use the \<br> HTML tag at the end of the line.<br>

### Escape Character is \

### Bold \*\*text\*\* and Italic \*text\*
This word is **bold** and this word is *italic*.<br>
Or you can use \_\_text\_\_ for __bold__ and \_text\_ for _italic_.<br>
Just like HTML tags \<strong> and \<em>.<br>

For ***bold and italic***, use \*\*\*text\*\*\*<br>

### Blockquotes
To create a blockquote, add a > in front of a paragraph.
> This should demonstrate a blockquote.

### Links
Here is a [link](https://duckduckgo.com "The best search engine for privacy").<br>
```
And here is how to make it:
Here is a [link](https://duckduckgo.com "The best search engine for privacy")
```

You can link to headings with custom IDs in the file by creating a standard link with a number sign (#) followed by the custom heading ID. These are commonly referred to as anchor links.<br>
[Heading IDs](#basic-syntax)<br>

To quickly turn a URL or email address into a link, enclose it in angle brackets.<br>
<https://www.markdownguide.org><br>
<fake@example.com><br>

### Horizontal rule
\*** or \--- or \__<br>
***
Just like HTML tag \<hr>

### Ordered Lists
To create an ordered list, add line items with numbers followed by periods. The numbers don’t have to be in numerical order, but the list should start with the number one.

1. First item
2. Second item
3. Third item
    1. Indented item 1
    2. Indented item 2
4. Fourth item

### Unordered Lists
To create an unordered list, add dashes (-), asterisks (*), or plus signs (+) in front of line items. Indent one or more items to create a nested list.
- First item
- Second item
- Third item
    - Indented item 1
    - Indented item 2
- Fourth item

To add another element in a list while preserving the continuity of the list, indent the element four spaces or one tab.<br>

* This is the first list item.
* Here's the second list item.

    I need to add another paragraph below the second list item.

* And here's the third list item.

### Code
To denote a word or phrase as code, enclose it in backticks (\`). <br>
This word would be a `code`.<br>

If the word or phrase you want to denote as code includes one or more backticks, you can escape it by enclosing the word or phrase in double backticks (\`\`).<br>
``This entire `sentence` is code.``

### Code Blocks
To create code blocks, indent every line of the block by at least four spaces or one tab.<br>
     code written here

Fenced Code Block<br>
```
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

Syntax Highlighting<br>
```json
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

### Images
To add an image, add an exclamation mark (!), followed by alt text in brackets, and the path or URL to the image asset in parentheses. You can optionally add a title in quotation marks after the path or URL.<br>

```
![The San Juan Mountains are beautiful!](/assets/images/san-juan-mountains.jpg "San Juan Mountains")
```

To add a link to an image, enclose the Markdown for the image in brackets, and then add the link in parentheses.<br>
```
[![An old rock in the desert](/assets/images/shiprock.jpg "Shiprock, New Mexico by Beau Rogers")](https://www.flickr.com/photos/beaurogers/31833779864/bXMYv)
```

### Using HTML
Many Markdown applications allow you to use HTML tags in Markdown-formatted text. This is helpful if you prefer certain HTML tags to Markdown syntax. For example, some people find it easier to use HTML tags for images. Using HTML is also helpful when you need to change the attributes of an element, like specifying the color of text or changing the width of an image.<br>

### Tables
To add a table, use three or more hyphens (---) to create each column’s header, and use pipes (|) to separate each column. For compatibility, you should also add a pipe on either end of the row.<br>

```
| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |
```
| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |

Alignment<br>
```
| Syntax      | Description | Test Text     |
| :---        |    :----:   |          ---: |
| Header      | Title       | Here's this   |
| Paragraph   | Text        | And more      |
```
| Syntax      | Description | Test Text     |
| :---        |    :----:   |          ---: |
| Header      | Title       | Here's this   |
| Paragraph   | Text        | And more      |


## Cheatsheets
https://www.markdownguide.org/cheat-sheet/<br>
https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet<br>
https://github.com/adam-p/markdown-here/wiki/Markdown-Here-Cheatsheet<br>

## Training material
https://www.markdownguide.org/basic-syntax/<br>
https://www.markdownguide.org/extended-syntax/<br>
https://github.github.com/gfm/    (GitHub Flavored Markdown)<br>
https://www.linkedin.com/learning/learning-markdown<br>

## Tools
<https://stackedit.io/> (In-browser Markdown editor)<br>
<https://dillinger.io/> (Editor)<br>
<https://blot.im/> (turns a folder into a website)<br>
<https://jekyllrb.com/> (static site generator that takes Markdown files and converts them to a website)<br>
