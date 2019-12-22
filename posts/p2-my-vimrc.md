---
layout: post
author: Le Tien Thanh
title: My Vimrc Configuration - Python IDE in Terminal
date: 22 12 2019
exclude: true
---

This post is a guide to setup a Vim as an IDE for Python. I will start with several basic configuration on syntax highlighting, indentation, code folding and commenting shortcut setting for Python in Vim. Then, I will introduct the way to setup several plugin for auto complete Python code. Finally, I will present the way to use NERDTree to keep track of file structure when you are in large project. The final result is we have a Python IDE that is nearly identical to SublimeText, but you will not have to leave the home row of your keyboard to reaching for your mouse.

### General Configuration
* * *

To enable syntax highlighting
```
if has("syntax")
  syntax on
endif
let python_highlight_all=1
```

Show matching parenthesis
```
set showmatch
```

Show the line numbers
```
set number
```

Set tabwidth 4 as PEP8 and expand tabs into spaces. Also keep indent when moving on to next line
```
set tabstop=4
set shiftwidth=4
set expandtab
filetype indent on
set autoindent
```

Code folding toggle using _Spacebar_ key
```
nnoremap <space> za
set foldmethod=indent
```

Enable comment code in Visual mode with _Highlight+'#'_ for comment and _Highlight+'-'+'#'_ for uncomment
```
vnoremap <silent> # :s/^/#/<cr>:noh<cr>
vnoremap <silent> -# :s/^#//<cr>:noh<cr>
```

I use Monokai theme to make vim look like SublimeText, since I had migrated from using SublimeText (5 years) to Vim. Noted that you have to follow the instruction to install the custom color theme [here](https://github.com/sickill/vim-monokai)
```
colorscheme monokai
```

Here is the tricky part...
### Vundle Plugin
```
" Vundle Plugin Manager
set nocompatible              " required
filetype off                  " required
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()
Plugin 'gmarik/Vundle.vim'
Bundle 'Valloric/YouCompleteMe'
Plugin 'vim-syntastic/syntastic'
Plugin 'nvie/vim-flake8'
Plugin 'scrooloose/nerdtree'
call vundle#end()            " required
filetype plugin indent on    " required

" Customize the YouCompleteMe
let g:ycm_autoclose_preview_window_after_completion=1
map <leader>g  :YcmCompleter GoToDefinitionElseDeclaration<CR>
```

### Extra to make it look like SublimeText
```

" NERDTree on startup vim
autocmd VimEnter * NERDTree

```
