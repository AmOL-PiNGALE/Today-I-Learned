
# Mastering Markdown

There is a reason why I am including this post here,

I have started this repo, to maintain list of thing which I learned day-to-day. But doing so I noticed I am doing lot of cleanup writting on the posts. The simple reason is, I don't know enough about how to write and format these markdown files properly. 

This post will highlight couple of important things for getting started and doing less mistakes. I will also point out what actual problem I faced. And how to overcome them.

So let's get started...

## What is Markdown?

[Markdown](https://daringfireball.net/projects/markdown/basics) is a way to style text on the web. You control the display of the document; formatting words as bold or italic, adding images, and creating lists are just a few of the things we can do with Markdown. Mostly, Markdown is just regular text with a few non-alphabetic characters thrown in, like `#` or `*`.

You can use Markdown most places around GitHub:

* [Gists](https://gist.github.com/)
* Comments in Issues and Pull Requests
* Files with the .md or .markdown extension


## Syntax guide

* Here’s an overview of Markdown syntax that you can use anywhere on GitHub.com or in your own text files.

### 1. Headers

    # This is an <h1> tag
    ## This is an <h2> tag
    ###### This is an <h6> tag

### 2. Emphasis

    *This text will be italic*
    _This will also be italic_

    **This text will be bold**
    __This will also be bold__

    _You **can** combine them_

### 3. Lists

#### Unordered

    * Item 1
    * Item 2
      * Item 2a
      * Item 2b

#### Ordered

    1. Item 1
    2. Item 2
    3. Item 3
       1. Item 3a
       2. Item 3b

### 4. Images

    ![GitHub Logo](/images/logo.png)
    Format: ![Alt Text](url)

### 5. Links

    http://github.com - automatic!
    [GitHub](http://github.com)

### 6. Blockquotes

    As Kanye West said:

    > We're living the future so
    > the present is our past.

### 7. Inline code

    I think you should use an
    `<addr>` element here instead.

## GitHub Flavored Markdown

* GitHub.com uses its own version of the Markdown syntax that provides an additional set of useful features, many of which make it easier to work with content on GitHub.com.
* Note that some features of GitHub Flavored Markdown are only available in the descriptions and comments of Issues and Pull Requests. These include @mentions as well as references to SHA-1 hashes, Issues, and Pull Requests. Task Lists are also available in Gist comments and in Gist Markdown files.

### 1. Syntax highlighting

Here’s an example of how you can use syntax highlighting with [GitHub Flavored Markdown](https://help.github.com/articles/basic-writing-and-formatting-syntax/):

    ```javascript
    function fancyAlert(arg) {
        if(arg) {
            $.facebox({div:'#foo'})
        }
    }
    ```

You can also simply indent your code by four spaces:

        function fancyAlert(arg) {
            if(arg) {
                $.facebox({div:'#foo'})
            }
        }

Here’s an example of Python code without syntax highlighting:

    def foo():
        if not bar:
            return True

### 2. Task Lists

    - [x] @mentions, #refs, [links](), **formatting**, and <del>tags</del> supported
    - [x] list syntax required (any unordered or ordered list supported)
    - [x] this is a complete item
    - [ ] this is an incomplete item

If you include a task list in the first comment of an Issue, you will get a handy progress indicator in your issue list. It also works in Pull Requests!

### 3. Tables

You can create tables by assembling a list of words and dividing them with hyphens - (for the first row), and then separating each column with a pipe |:

    First Header | Second Header
    ------------ | -------------
    Content from cell 1 | Content from cell 2
    Content in the first column | Content in the second column
    
Would become:

First Header | Second Header
------------ | -------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column
</br>

### 4. SHA references

Any reference to a commit’s SHA-1 hash will be automatically converted into a link to that commit on GitHub.

    16c999e8c71134401a78d4d46435517b2271d6ac
    mojombo@16c999e8c71134401a78d4d46435517b2271d6ac
    mojombo/github-flavored-markdown@16c999e8c71134401a78d4d46435517b2271d6ac

### 5. Issue references within a repository

Any number that refers to an Issue or Pull Request will be automatically converted into a link.

    #1
    mojombo#1
    mojombo/github-flavored-markdown#1

### 6. Username @mentions

Typing an `@` symbol, followed by a username, will notify that person to come and view the comment. This is called an “@mention”, because you’re mentioning the individual. You can also @mention teams within an organization.

### 7. Automatic linking for URLs

Any URL (like `http://www.github.com/`) will be automatically converted into a clickable link.

### 8. Strikethrough

Any word wrapped with two tildes (like `~~this~~`) will appear crossed out.

### 9. Emoji

GitHub supports [emoji](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#using-emoji)!

To see a list of every image we support, check out the [Emoji Cheat Sheet](https://github.com/ikatyang/emoji-cheat-sheet).


## References

1. [https://guides.github.com/features/mastering-markdown/](https://guides.github.com/features/mastering-markdown/)
2. [https://docs.github.com/en/github/writing-on-github](https://docs.github.com/en/github/writing-on-github)