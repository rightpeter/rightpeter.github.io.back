---
layout: post
category: note
tagline: "Vim Build"
tags: [Vim]
---
{% include JB/setup %}

# [Python syntax highlighting](http://www.vim.org/scripts/script.php?script_id=790)

**Install details:**

Place [python.vim](http://www.vim.org/scripts/download_script.php?src_id=21056) file in ~/.vim/syntax/ folder.

- - - -
- - - -

# [Markdown Vim Highlighting](http://www.vim.org/scripts/script.php?script_id=2882)

**Install Details**

Easy! Just open gzipball file with Vim (of course!) and use command :source %.
All files will be extracted in your Vim home directory.

`$ vim markdown-<version>.vba.gz +"source % | quit!"`

Please, visit
[https://github.com/hallison/vim-markdown/tree/changes](https://github.com/hallison/vim-markdown/tree/changes) for more information.

- - - -
- - - -

# Mapping keys in Vim
Reference to [Mapping keys in Vim -
Tutorial](http://vim.wikia.com/wiki/Mapping_keys_in_Vim_-_Tutorial_(Part_1))

**Introduction**

- - - -

Key mapping refers to creating a chortcut for repeating a sequence of keys or
commands. You can map keys to execute frequently used key sequences or to
invoke an Ex command or to invoke a Vim function or to invoke external
commands. Using key maps you can define your own Vim commands.

Vim supports several editing modes - normal, insert, replace, visual, select,
command-line and operator-pending. You can map a key to work in all or some of
these modes.

The general syntax of a map command is:

    {cmd} {attr} {lhs} {rhs}

    where
    {cmd}  is one of ':map', ':map!', ':nmap', ':vmap', ':imap',
           ':cmap', ':smap', ':xmap', ':omap', ':lmap', etc.
    {attr} is optional and one or more of the following: <buffer>, <silent>,
           <expr> <script>, <unique> and <special>.
           More than one attribute can be specified to a map.
    {lhs}  left hand side, is a sequence of one or more keys that you will use
           in your new shortcut.
    {rhs}  right hand side, is the sequence of keys that the {lhs} shortcut keys
           will execute when entered.

Examples:

    map <F2> :echo 'Current time is ' . strftime('%c')<CR>
    map! <F3> <C-R>=strftime('%c')<CR>
    nnoremap <silent> <F2> :lchdir %:p:h<CR>:pwd<CR>

The first step in creating a map is to decide the sequence of keys that needs
to be mapped. When you invoke a map, Vim will execute the sequence of keys as
though you entered it from the keyboard. You can do this by manually entering
the keysequence and verifying that they perform the desired operation.

The second step is to decide the editing mode (insert mode, visual mode,
command-line mode, normal mode, etc.) in which the map should work. Instead of
creating a map that works in all the modes, it is better to define the map that
works only in selected modes.

The third step is to find an unused key sequence that can be used to invoke the
map. You can invoke a map using either a single key or a sequence of keys.
[:help
map-which-keys](http://vimdoc.sourceforge.net/htmldoc/map.html#map-which-keys)

The above are explained in more detail in the following sections.
