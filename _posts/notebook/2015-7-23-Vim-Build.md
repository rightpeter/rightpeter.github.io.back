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

# [Markdown Vim Highlighting](http://www.vim.org/scripts/script.php?script_id=2882)

**Install Details**

Easy! Just open gzipball file with Vim (of course!) and use command :source %.
All files will be extracted in your Vim home directory.

`$ vim markdown-<version>.vba.gz +"source % | quit!"`

Please, visit
[https://github.com/hallison/vim-markdown/tree/changes](https://github.com/hallison/vim-markdown/tree/changes) for more information.

- - - -

# Mapping keys in Vim
Reference to [Mapping keys in Vim -
Tutorial](http://vim.wikia.com/wiki/Mapping_keys_in_Vim_-_Tutorial_(Part_1))

**Introduction**

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

**Finding unused keys**

In your private maps you should use key sequences that are not used by Vim and
by other Vim plugins. [:help
map-which-keys](http://vimdoc.sourceforge.net/htmldoc/map.html#map-which-keys)

Many of the key sequences that you can enter from the keyboard are used by Vim
to implement the various internal commands. If you use a key sequence in your
map that is already used by Vim, then you will not be able to use the
functionality provided by Vim for that key sequence. To get a list of the key
sequences used by Vim, read the following help topic:

    :help index.txt

If you don't use some Vim functionality invoked by a particular key sequence or
you have an alternate key sequence to use that functionality then you can use
that key sequence in your maps.

Some of the key sequences may be used by the existing Vim scripts and plugins.
To display the list of keys that ar currently mapped, use the following
command:

    :map
    :map!

To determine the script or plugin that defines a map for a key sequence, use
the following command.

    :verbose map <key>

In the above command, replace <key> with the desired key sequence. For example,
to list all the locations where maps beginning with "," are defined, use the
following command:

    :verbose map ,

Try to use an unused key sequence in your maps. Typically, the <F2>, <F3>, ...
etc function keys are unused. The function keys in combination with Control,
Alt and Shift can also be used. But some of the key combinations may not work
in all the terminal emulators. Most of the key combinations should work in GUI
Vim.

You can alse prefix the desired key sequence with a backslash (\) or comma (,)
or underscore (\_), etc. and use that in your maps.

Note that you cannot map the Shift or Alt or Ctrl keys alone as they are key
modifiers. You have to combine these key modifiers with other keys to create a
map.

You should not use a frequently used Vim key sequence at the start of your map.
For example, you should not start your normal mode map key sequence with "j" or
"k" or "l" or "h". These keys are used for moving the cursor in normal mode. If
you use any of these keys at the begining of your maps, then you will observe a
delay when you enter a single "j" or "k" or "l" or "h".

**Using maps in Vim plugins and scripts**

A Vim plugin or script can define new key maps to let the user invoke the
commands and functions provided by the plugin. A Vim plugin can alse invoke key
maps defined by other Vim plugins.

A plugin can choose to map any available key. But to avoid surprising
(annoying) the user, it is better not to use the keys that already have
pre-defined functionality in Vim.

In a Vim plugin, the ":normal" command is used to execute normal mode commands.
For example, the "gqip" normal mode command is used to format a paragraph. To
invoke this command from a Vim plugin, the following line can be used:

    normal gqip

If any of the keys in "gqip" is mapped, then the mapped key sequence will be
executed. This may change the expected behavior of the "gqip" command. To avoid
this, add the "!" suffix to the "normal" command:

    normal! gqip

With the "!" suffix, the "normal" command executes the built-in functionality
provided by Vim for the specified sequence of keys.

To invoke a script local function, defined with the "s:" prefix, from a map,
you have to prefix the function name with <SID>. You cannot use the "s:" prefix
for the script-local function, as the map will be invoked from outside of the
script context.

    :inoremap <expr> <C-U> <SID>InsertFunc()

A plugin may map one or more keys to easily invoke the functionality provided
by the plugin. In the plugin functions used by these types of maps, it is
advisable not to alter user Vim option settings, register contents and marks.
Otherwise, the user will be surprised to see that some options are changed
after invoking a plugin provided map.

**Map leader**

If the key maps provided by all the Vim plugins start with a same key, then it
is easier for a user to distinguish between his own key maps and the ones
privided by plugins. To facilitate this, Vim provides a special keyword that
can be used in a map command.
