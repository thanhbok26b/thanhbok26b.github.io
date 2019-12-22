---
layout: post
author: Le Tien Thanh
title: My Vimrc Configuration - Python IDE in Terminal
date: 22 12 2019
---

### General Configuration
```
" enable syntax highlighting
if has("syntax")
  syntax on
endif

" show line numbers
set number

" set tabs to have 4 spaces
set tabstop=4
set shiftwidth=4

" expand tabs into spaces
set expandtab

" keep indent when moving to next line
filetype indent on
set autoindent

" show matching parenthesis
set showmatch

" enable all Python syntax highlighting features
let python_highlight_all=1

" code folding
nnoremap <space> za
set foldmethod=indent
```

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
" Monokai theme
colorscheme monokai

" NERDTree on startup vim
autocmd VimEnter * NERDTree

" Enable comment in visual mode
vnoremap <silent> # :s/^/#/<cr>:noh<cr>
vnoremap <silent> -# :s/^#//<cr>:noh<cr>
```
