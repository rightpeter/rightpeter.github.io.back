# Horizontal Rules

You can produce a horizontal line with any of the following codes:

>`* * *`

>`***`

>`*****`

>`- - - -`

>`----------------`

The output looks like this:

* * *

***

*****

- - - -

------------------

# Markdown Vim Highlighting

[Vim Hight Lighting](http://www.vim.org/scripts/script.php?script_id=2882)

## Install Details

Easy! Just open gzipball file with Vim (of course!) and use command :source %.
All files will be extracted in your Vim home directory.

>`$ vim markdown-<version>.vba.gz +"source % | quit!"`

Please, visit
[https://github.com/hallison/vim-markdown/tree/changes](https://github.com/hallison/vim-markdown/tree/changes) for more information.

# Fenced code blocks

Standard Markdown converts text with four spaces at the beginning of each line
into a code block; GFM alse supports fenced blocks. Just wrap your code in
`````` (as shown below) and you won't need to indent it by four spaces. Note
that although fenced code blocks don't have to be preceded by a blank line -
unlike indented code blocks - we recommend placing a blank line before them to
make the raw Markdown easier to read.
