filetype plugin indent on
set nocompatible

" Security
set modelines=0

" Tabs/spaces
set tabstop=4
set shiftwidth=4
set softtabstop=4
set expandtab

" Basic options
set encoding=utf-8
set scrolloff=3
set autoindent
set showmode
set showcmd
set hidden
set wildmenu
set wildmode=list:longest
set visualbell
set cursorline
set ttyfast
set ruler
set backspace=indent,eol,start
set laststatus=2
set relativenumber
set undofile
set undoreload=10000

" Backups
set backupdir=~/.vim/tmp/backup// " backups
set directory=~/.vim/tmp/swap//
set backup

" Leader
let mapleader = ","

" Make Y not dumb
nnoremap Y y$

" Searching
nnoremap <leader>1 yypVr=
nnoremap / /\v
vnoremap / /\v
set ignorecase
set smartcase
set gdefault
set incsearch
set showmatch
set hlsearch
nnoremap <leader><space> :noh<cr>

" Soft/hard wrapping
set wrap
set textwidth=79
set formatoptions=qrn1
set colorcolumn=85

" Use the same symbols as TextMate for tabstops and EOLs
set list
set listchars=tab:▸\ ,eol:¬

" Color scheme (terminal)
syntax on
set background=dark
colorscheme delek

" Use the damn hjkl keys
nnoremap <up> <nop>
nnoremap <down> <nop>
nnoremap <left> <nop>
nnoremap <right> <nop>
inoremap <up> <nop>
inoremap <down> <nop>
inoremap <left> <nop>
inoremap <right> <nop>

" And make them fucking work, too
nnoremap j gj
nnoremap k gk

" Easy buffer navigation
nnoremap <C-h> <C-w>h
nnoremap <C-j> <C-w>j
nnoremap <C-k> <C-w>k
nnoremap <C-l> <C-w>l
nnoremap <leader>w <C-w>v<C-w>l

" Disable F1
set fuoptions=maxvert,maxhorz
inoremap <F1> <ESC>:set invfullscreen<CR>a
nnoremap <F1> :set invfullscreen<CR>
vnoremap <F1> :set invfullscreen<CR>

" Folding
set foldlevelstart=0
nnoremap <Space> za
vnoremap <Space> za
noremap <leader>ft Vatzf

function! MyFoldText()
    let line = getline(v:foldstart)

    let nucolwidth = &fdc + &number * &numberwidth
    let windowwidth = winwidth(0) - nucolwidth - 3
    let foldedlinecount = v:foldend - v:foldstart

    " expand tabs into spaces
    let onetab = strpart('          ', 0, &tabstop)
    let line = substitute(line, '\t', onetab, 'g')

    let line = strpart(line, 0, windowwidth - 2 -len(foldedlinecount))
    let fillcharcount = windowwidth - len(line) - len(foldedlinecount) - 4
    return line . '…' . repeat(" ",fillcharcount) . foldedlinecount . '…' . ' '
endfunction
set foldtext=MyFoldText()

" Various syntax stuff
au BufNewFile,BufRead *.less set filetype=less
au BufNewFile,BufRead *.scss set filetype=scss

au BufNewFile,BufRead *.vim set foldmethod=marker

" Sort CSS
map <leader>S ?{<CR>jV/^\s*\}?$<CR>k:sort<CR>:noh<CR>

" Clean whitespace
map <leader>W :%s/\s\+$//<cr>:let @/=''<CR>

" Formatting, TextMate-style
map <leader>q gqip

nmap <leader>m :make<CR>

" Easier linewise reselection
nnoremap <leader>v V`]

" Edit vim stuff
nnoremap <leader>ev <C-w>s<C-w>j<C-w>L:e $MYVIMRC<cr>
"nnoremap <leader>es <C-w>s<C-w>j<C-w>L:e ~/.vim/snippets/<cr>

" Rainbows!
nmap <leader>R :RainbowParenthesesToggle<CR>

" Sudo to write
cmap w!! w !sudo tee % >/dev/null

" Paste mode
nnoremap <leader>pp :set invpaste paste?<CR>
set pastetoggle=<leader>pp
set showmode

" Easy filetype switching
nnoremap _dt :set ft=htmldjango<CR>
nnoremap _pd :set ft=python.django<CR>

" Save when losing focus
au FocusLost * :wa

" Statusline
set statusline=%F%m%r%h%w\ [FORMAT=%{&ff}]\ [TYPE=%Y]\ [BRANCH=%{fugitive#statusline()}]\ [POS=%04l,%04v][%p%%]\ [LEN=%L]

" Show syntax highlighting groups for word under cursor
nmap <C-S> :call SynStack()<CR>
function! SynStack()
  if !exists("*synstack")
    return
  endif
  echo map(synstack(line('.'), col('.')), 'synIDattr(v:val, "name")')
endfunc


if has('gui_running')
    set guifont=Menlo:h12
    colorscheme molokai
    set background=dark

    set go-=T
    set go-=l
    set go-=L
    set go-=r
    set go-=R

"    if has('gui_macvim')
"        macmenu &File.New\ Tab key=<nop>
"        map <leader>t <Plug>PeepOpen
"    end

    let g:sparkupExecuteMapping = '<D-e>'

    highlight SpellBad term=underline gui=undercurl guisp=Orange
endif

