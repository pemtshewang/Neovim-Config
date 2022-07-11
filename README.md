# My neovim config { init.vim }

- Thanks Steven Losh for his wonderful book *Learn Vimscript the hardway*
- I am able to create my own vimrc and neccesssary nvim key mappings that had helped me a lot

```vim
set relativenumber
set hlsearch
set autoindent
let mapleader=','

inoremap jk <esc>
inoremap <esc> <nop>
inoremap <leader>ev <esc>:vsplit $MYVIMRC<cr>
inoremap <leader>sv <esc>:source $MYVIMRC<cr>
inoremap <leader>ww <esc>:w<cr>
inoremap <leader>wq <esc>:wq<cr>
inoremap <leader>qq <esc>:q!<cr>
inoremap <leader>qq <esc>:q!<cr>
nnoremap ; :
" inoremap <Up> <nop>
" inoremap <Down> <nop>
" inoremap <Left> <nop>
" inoremap <Right> <nop>
nnoremap : <nop>
inoremap <BS> <nop>
inoremap <leader>n <esc>:NERDTreeToggle<cr>
nnoremap <leader>n <esc>:NERDTreeToggle<cr>
onoremap p i(

" abbrev
iabbrev main #include<iostream><cr>using namespace std;<cr>int main(int argc,char *argv[]){<cr><cr><cr>return 0;<cr>}

call plug#begin('~/.config/nvim/autoload/plugged')

" Nerdtree as File Explorer
Plug 'https://github.com/scrooloose/nerdtree'

" Coimmentary Vim
Plug 'tpope/vim-commentary'

"Markdown syntax highlighting
Plug 'vim-pandoc/vim-pandoc-syntax'

" if you don't have node and yarn, use pre build
Plug 'iamcco/markdown-preview.nvim', { 'do': 'cd app && yarn install' }
" tabular plugin is used to format tables
Plug 'godlygeek/tabular'

"Python highlight
Plug 'vim-python/python-syntax'

" Any valid git URL is allowed
"Air line themes for status line
Plug 'vim-airline/vim-airline'
Plug 'vim-airline/vim-airline-themes'
"tmux
Plug 'https://github.com/hkupty/nvimux.git'
"Scrollingbar
Plug 'karb94/neoscroll.nvim'

" Optional but recommended
" Plug 'nvim-treesitter/nvim-treesitter'
Plug 'lewis6991/spellsitter.nvim'

"Copilot nvim setup
Plug 'https://github.com/github/copilot.vim.git'

" Github theme
Plug 'projekt0n/github-nvim-theme'
Plug 'tiagovla/tokyodark.nvim'

"Dependency for telescope
Plug 'nvim-lua/plenary.nvim'
Plug 'https://github.com/sharkdp/fd'
Plug 'https://github.com/BurntSushi/ripgrep'

"Telescope for fuzzy file finder
Plug 'nvim-telescope/telescope.nvim'

" For git
Plug 'tpope/vim-fugitive'

"Floating terminal
Plug 'voldikss/vim-floaterm'

call plug#end()

" Set internal encoding of vim, not needed on neovim, since coc.nvim using some
" unicode characters in the file autoload/float.vim
set encoding=utf-8

" Some servers have issues with backup files, see #649.
set nobackup
set nowritebackup

" Give more space for displaying messages.
set cmdheight=2

" Having longer updatetime (default is 4000 ms = 4 s) leads to noticeable
" delays and poor user experience.
set updatetime=300

" Don't pass messages to |ins-completion-menu|.
set shortmess+=c

" Making the telescope see andromeda
inoremap <leader>t <esc>:Telescope<cr>

" Floatterm
"Opening the terminal
inoremap <leader>ft <esc>:FloatermNew --height=0.6 --width=0.4 --wintype=float --name=user --position=topright <cr>

"Compiling gcc
inoremap <leader>gcc <esc>:FloatermNew --height=0.6 --width=0.4 --wintype=float --name=gcc --position=topright --autoclose=0 gcc % -o %< && ./%<<cr>

"Compiling g++
inoremap <leader>gpp <esc>:FloatermNew --height=0.6 --width=0.4 --wintype=float --name=g++ --position=topright --autoclose=0 g++ % -o %< && ./%<<cr>

"Interpret Python
inoremap <leader>pp <esc>:FloatermNew --height=0.6 --width=0.4 --wintype=float --name=python --position=topright --autoclose=0 python3 % <cr>

nnoremap <leader>qq :q!<cr>

"snippet
augroup IFF
  autocmd FileType python :iabbrev <buffer> iff if:<Left>
  autocmd FileType javascript :iabbrev <buffer> iff if ()<Left>
augroup END

augroup pandoc_syntax
    au! BufNewFile,BufFilePre,BufRead *.md set filetype=markdown.pandoc
augroup END
```
