---
layout: post
title:  "What I wish I knew when I started learning Vim"
date:   2021-12-27 18:05:43 -0500
categories: vim
---
`vim` is a hugely influential text editor developed in the 1990's by Bram
Moolenaar. Unlike most modern text editors, there was no way to use a mouse.
Everything was done via keyboard shortcuts. This means two things: firstly,
you'll be able to navigate more quickly, as you won't ever have to move your
hand to the mouse. Secondly, you have to memorize a ton of shortcuts in order
to make even basic use of the text editor. Such an archaic editor still enjoys
widespread use in the software development community because it allows them to
navigate files much more easily. 

* TOC
{:toc}

# Unbind your arrow keys!
This one is pretty important. `vim`'s default mode of navigation is via
the `h`, `j`, `k`, and `l` commands.
- `h` - move the cursor to the left
- `j` - move the cursor downwards
- `k` - move the cursor upwards
- `l` - move the cursor rightwards

## Why?
Unbinding your arrow keys may sound counter-intuitive at first - why would I
want to disable part of my keyboard? I assure you the benefit is worth it. If
you don't unbind your arrow keys, you'll continue using them all the time,
meaning you won't start to pick up on `vim` and all of its capabilities.

## How?
You'll need to execute some commands in order to unbind your arrow keys. If
you don't know what a `.vimrc` file is, I'd suggest you look it up, as it's
an important concept. You want to modify your `.vimrc` file, appending the
following lines:
{% highlight vimscript %}
noremap <Up> <Nop>
noremap <Down> <Nop>
noremap <Left> <Nop>
noremap <Right> <Nop>
{% endhighlight %}
This will disable the usage of the arrow keys. If you're using it correctly,
you'll never need to use your arrow keys anyways - they'd just slow you down.

# It's not easy
Learning how to properly use `vim` isn't easy - I've been using it for over
a year now, and I'm still learning more and more each day. When you start
using `vim`, development will be slow. You'll spend a lot of time figuring out
how to do basic operations that you'd previously done via the mouse. It may
take a month (or two) to get back to your pre-Vim speed of work.

Don't be discouraged if you don't immediately pick it up. It's the nerdiest of
nerdy text editors - hundreds of obscure bindings and absolutely no tutorial
on how to use it. If you're considering stopping the process of learning how
to use `vim`, I'd encourage you to... not do that. It's definitely worth it.

# Learn to use Google
I'm sure you've heard all about how important Google is for any developer.
The same is true for `vim` - there's a ton of resources online that you can
consult for help. A few solid recommendations:
- [Vim Tips][vim_tips] - wiki containing an abundance of information about
  vim - useful learning resource.
- [Vim Cheat Sheet][vim_cheat_sheet] - incredibly simple webpage that displays
  nearly all the important bindings in `vim`.
- [vi Complete Key Binding List][vi_binds] - key bindings for vim's predecessor,
  `vi`. Most of these carry over to `vim`.

If you're trying to do something that seems simple but is incredibly
time-consuming, there's probably a better way to be doing it. `vim` has
loads of useful features, such as [macros][macros] and [visual block mode][vbm].

# Figure out the different modes
There's a couple of modes `vim` can be in:
- `normal`: the default mode of `vim`. In this, you can interact with `vim`
  via commands such as `hjkl`.
- `insert`: this is the mode of `vim` that allows you to actually insert text.
  You'll need to be in insert mode to make very much progress at all.
- `visual`: this is a mode that allows you to create a selection and view
  that aforementioned selection. You can perform manipulation on large selections
  of text quite easily with visual mode.
- `visual_line`: same as `visual` but on a line-by-line basis.
- `visual_block`: same as `visual` but on a column-by-column basis.

## Change your escape binding
Another line you can add to your `.vimrc`:
{% highlight vimscript %}
inoremap jk <Esc>
{% endhighlight %}
`inoremap` will apply a non-recursive binding exclusively to insert mode.
Whenever you type the letters `jk` while in insert mode, you'll exit insert
mode and go back into normal mode. 

Although this is rather subjective, `jk` is much easier to access than the
escape key, allowing you to save time when typing. If you plan on doing this,
you should do it early, because entering normal mode is one of the operations
you'll be doing the most, and it's hard to retrain muscle memory.

# Customize your vimrc
`.vimrc` is the main method of controlling `vim`'s default behavior. Every
time you open a new instance of `vim`, the code in the `.vimrc` file will
be executed. This allows you to set up bindings and configurations that are
automatically applied whenever you open up `vim`. This is, for example, where
you'd put the vimscript to map `jk` to `<Esc>`.

## Settings
`vim` has a lot of settings, but some of them are... nearly essential.
{% highlight vimscript %}
set tabstop=4
set softtabstop=4
set shiftwidth=4
set expandtab
set ai
set noerrorbells
set novisualbell
{% endhighlight %}

## Bindings
You'll want to find what bindings YOU like - after all, it's about what you're
the most comfortable with. There are some bindings I think everyone should
use, however.
{% highlight vimscript %}
noremap < <gv
noremap > >gv
{% endhighlight %}

[vim_tips]: https://vim.fandom.com/wiki/Vim_Tips_Wiki
[vim_cheat_sheet]: https://vim.rtorr.com
[vi_binds]: https://hea-www.harvard.edu/~fine/Tech/vi.html
[macros]: https://vim.fandom.com/wiki/Macros
[vbm]: https://stackoverflow.com/questions/41670493/visual-block-edit-in-vim
