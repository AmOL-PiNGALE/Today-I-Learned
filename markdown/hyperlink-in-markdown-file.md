
# Hyperlink in Markdown File

How do I create a hyperlink in the README file in my GitHub account which would redirect to a new page containing the project explanation?

Follow the below format
ex: [Text to show](actual_URL to navigate)

    [Lets go to Quora](https://www.quora.com)

Would become:

[Lets go to Quora](https://www.quora.com)

</br>

### Using Raw Markdown
------------------------------------
You can also manually type the raw markdown text for a link. To embed links into a topic you can either use the markdown syntax like this:</br>

    [Go to the Support Web Site](https://support.west-wind.com)

or for local links using relative paths
[text to show](relative url to .md file)

    [README file](../README.md)


### HTML Syntax
------------------------------------
Markdown also supports raw HTML so you can also use raw HTML text to embed links. This is useful if you require target links or need to add alignment styling.</br>

    format - <a href="file_name">Text to show</a>
    ex. <a href=".../README.md" target="_top">README Page</a>

would become,

<a href=".../README.md" target="_top">README Page</a>