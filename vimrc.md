# Vimrc

```text
" Specify a directory for plugins
" - For Neovim: ~/.local/share/nvim/plugged
" - Avoid using standard Vim directory names like 'plugin'
call plug#begin()

" Make sure you use single quotes

" " Shorthand notation; fetches https://github.com/junegunn/vim-easy-align
" Plug 'junegunn/vim-easy-align'
" 
" " Any valid git URL is allowed
" Plug 'https://github.com/junegunn/vim-github-dashboard.git'
" 
" " Multiple Plug commands can be written in a single line using | separators
" Plug 'SirVer/ultisnips' | Plug 'honza/vim-snippets'
" 
" " On-demand loading
" Plug 'scrooloose/nerdtree', { 'on':  'NERDTreeToggle' }
" Plug 'tpope/vim-fireplace', { 'for': 'clojure' }
" 
" " Using a non-master branch
" Plug 'rdnetto/YCM-Generator', { 'branch': 'stable' }
" 
" " Using a tagged release; wildcard allowed (requires git 1.9.2 or above)
" Plug 'fatih/vim-go', { 'tag': '*' }
" 
" " Plugin options
" Plug 'nsf/gocode', { 'tag': 'v.20150303', 'rtp': 'vim' }
" 
" " Plugin outside ~/.vim/plugged with post-update hook
" Plug 'junegunn/fzf', { 'dir': '~/.fzf', 'do': './install --all' }
" 
" " Unmanaged plugin (manually installed and updated)
" Plug '~/my-prototype-plugin'

" status line
Plug 'vim-airline/vim-airline'
" auto comment
Plug 'scrooloose/nerdcommenter'
" files tree
Plug 'scrooloose/nerdtree'
" show git info in nerdtree window
Plug 'Xuyuanp/nerdtree-git-plugin'
" ctrlP like sublime to search everywhere smart
Plug 'kien/ctrlp.vim'
" chinese doc
Plug 'yianwillis/vimcdoc'
" git
Plug 'tpope/vim-fugitive'
" format
Plug 'Chiel92/vim-autoformat'
" hlsl syntax highlighting
Plug 'beyondmarc/hlsl.vim'
" glsl syntax highlighting
Plug 'tikhomirov/vim-glsl'
" cg syntax highlighting
Plug 'vim-scripts/cg.vim'
" unity shader syntax highlighting
Plug 'vim-scripts/ShaderHighLight'
" markdown highlight
Plug 'plasticboy/vim-markdown'
" markdown preview
" Plug 'iamcco/markdown-preview.vim'
" " evernote
" Plug 'LER0ever/EverVim'
" YouCompleteMe
" Plug 'Valloric/YouCompleteMe'
" " Lua file type plug-in for the Vim text editor
" Plug 'xolox/vim-lua-ftplugin'
" " Miscellaneous auto-load Vim scripts
" Plug 'xolox/vim-misc'
" vim-polyglot: A collection of language packs for Vim.
Plug 'sheerun/vim-polyglot'

" Initialize plugin system
call plug#end()








"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" => VIM user interface
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" 这个leader就映射为逗号“，”
let mapleader = ","
let g:mapleader = ","
" Set 7 lines to the cursor - when moving vertically using j/k
set so=7

" Avoid garbled characters in Chinese language windows OS
" let $LANG='en' 
" set langmenu=en
" source $VIMRUNTIME/delmenu.vim
" source $VIMRUNTIME/menu.vim

" Ignore compiled files
set wildignore=*.o,*~,*.pyc
if has("win16") || has("win32")
    set wildignore+=.git\*,.hg\*,.svn\*
else
    set wildignore+=*/.git/*,*/.hg/*,*/.svn/*,*/.DS_Store
endif

"Always show current position
set ruler

" Height of the command bar
set cmdheight=2

" Configure backspace so it acts as it should act
set backspace=eol,start,indent
set whichwrap+=<,>,h,l

" Highlight search results
set hlsearch

" Ignore case when searching
set ignorecase

" When searching try to be smart about cases 
set smartcase

" Makes search act like search in modern browsers
set incsearch 

" Don't redraw while executing macros (good performance config)
set lazyredraw 

" For regular expressions turn magic on
set magic

" Show matching brackets when text indicator is over them
set showmatch 

" How many tenths of a second to blink when matching brackets
set mat=2

" No annoying sound on errors
set noerrorbells
set novisualbell
set vb t_vb=
set tm=500

" Add a bit extra margin to the left
" set foldcolumn=1

"显示行号
set number

"显示TAB健
set list
set listchars=tab:>-,trail:-

"去掉有关vi一致性模式，避免以前版本的一些bug和局限 
set nocp

"设定文件浏览器目录为当前目录 
set bsdir=buffer
"自动切换当前目录为当前文件所在的目录 
set autochdir
"自动重新加载外部修改内容 
"set autoread 

" Add spaces after comment delimiters by default
let g:NERDSpaceDelims = 1

" Use compact syntax for prettified multi-line comments
let g:NERDCompactSexyComs = 0

" Align line-wise comment delimiters flush left instead of following code indentation
let g:NERDDefaultAlign = 'left'

" Set a language to use its alternate delimiters by default
" let g:NERDAltDelims_java = 1

" Add your own custom formats or override the defaults
" let g:NERDCustomDelimiters = { 'c': { 'left': '/**','right': '*/' } }

" Allow commenting and inverting empty lines (useful when commenting a region)
let g:NERDCommentEmptyLines = 1

" Enable trimming of trailing whitespace when uncommenting
let g:NERDTrimTrailingWhitespace = 1



"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" => user config
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" small
set pythonthreedll=python36.dll

" let g:molokai_original = 1
" let g:rehash256 = 1

" Sets how many lines of history VIM has to remember
set history=1000

" Enable filetype plugins
filetype plugin on
filetype indent on

" Set to auto read when a file is changed from the outside
set autoread

" Fast saving
map <leader>w :w!<cr>
" Fast quit
map <leader>q :q!<cr>
" file encoding
set encoding=utf-8  

set fileencodings=utf-8,chinese,latin-1  

if has("win32")  

    set fileencoding=chinese  
    "解决菜单乱码  

    source $VIMRUNTIME/delmenu.vim  

    source $VIMRUNTIME/menu.vim  

    "解决consle输出乱码  

    language messages zh_CN.utf-8

else  

    set fileencoding=utf-8  
endif  





"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" => Hot Key
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" use <F5> to compile file
map <F5> :call CompileFile()<CR>
imap <F5> <ESC>:call CompileFile()<CR>
" use gcc
map <leader>gcc :call CompileRunGpp()<CR>
" use clang
map <leader>clang :call CompileRunClangpp()<CR>

" compile file
func! CompileFile()
    exec "w"
    exec "cd %:p:h"
    if &filetype == 'c'
        :call CompileRunC()
    elseif &filetype == 'cpp' || &filetype == 'cc' || &filetype == 'cxx'
        :call CompileRunCpp()
    elseif &filetype == 'java' 
        :call CompileRunJava()
    elseif &filetype == 'python'
        :call CompileRunPython3()
    elseif &filetype == 'sh'
        :call CompileRunShell()
    elseif &filetype == 'lua'
        :call CompileRunLua()
    endif
endfunc

" compile and run c
func! CompileRunC()
    :call CompileRunClangpp()
endfunc

" compile and run cpp
func! CompileRunCpp()
    :call CompileRunClangpp()
endfunc

" compile and run with clang
func! CompileRunClangpp()
    " exec "! %<.exe"
    if has("win32")
        exec "!clang++ % -o %<.exe & %<.exe"
        exec "! del %<.exe"
    else
        exec "!clang++ % -o %<.exe & ./%<"
        exec "! del %<"
    endif
endfunc

" run java
func! CompileRunJava()
    exec "!javac % & java %< & del %<.class" 
    " exec "!java %< & del %<.class"
    " exec "! del %<.class"
endfunc

" use gcc to compile
func! CompileRunGpp()
    exec "!g++ % -o %<"
    exec "! ./%<"
endfunc

" run shell script
func! CompileRunShell()
    :!./%
endfunc

func! CompileRunLua()
    exec "! lua %"
endfunc

" run python3
func! CompileRunPython3()
    exec "! python %"
endfunc
" use ,] to comment and ,[ to uncomment
" function! Comment()
    " :autocmd FileType java map <leader>] I// <esc>j^
    " :autocmd FileType java map <leader>[ 0xxx<Esc>j^
    " :autocmd FileType c map <leader>] I// <esc>j^
    " :autocmd FileType c map <leader>[ 0xxx<Esc>j^
    " :autocmd FileType cc map <leader>] I// <esc>j^
    " :autocmd FileType cc map <leader>[ 0xxx<Esc>j^
    " :autocmd FileType cpp map <leader>] I// <esc>j^
    " :autocmd FileType cpp map <leader>[ 0xxx<Esc>j^
    " :autocmd FileType cxx map <leader>] I// <esc>j^
    " :autocmd FileType cxx map <leader>[ 0xxx<Esc>j^
    " :autocmd FileType h map <leader>] I// <esc>j^
    " :autocmd FileType h map <leader>[ 0xxx<Esc>j^
    " :autocmd FileType python map <leader>] I# <Esc>j^
    " :autocmd FileType python map <leader>[ 0xx<Esc>j^
    " :autocmd FileType sh map <leader>] I# <Esc>j^
    " :autocmd FileType sh map <leader>[ 0xx<Esc>j^
    " :autocmd FileType vim map <leader>] I" <Esc>j^
    " :autocmd FileType vim map <leader>[ 0xx<Esc>j^
" endfunc
" call Comment()

" use F11 to enter fullscreen mode
map <F11> :call libcallnr("gvimfullscreen_64.dll", "ToggleFullScreen", 0)<CR>



"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" => Colors and Fonts
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" Enable syntax highlighting
syntax enable
" color theme
colorscheme molokai

" Enable 256 colors palette in Gnome Terminal
" if $COLORTERM == 'gnome-terminal'
"     set t_Co=256
" endif
" 
" try
    " colorscheme desert
" catch
" endtry
" 
" set background=dark

" Set extra options when running in GUI mode
if has("gui_running")
    set guioptions-=T
    set guioptions-=m
    set guioptions-=e
    set t_Co=256
    set guitablabel=%M\ %t
endif

" Use Unix as the standard file type
set ffs=unix,dos,mac

" set font
set guifont=Courier\ New:h14



"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" => Files, backups and undo
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" Turn backup off, since most stuff is in SVN, git et.c anyway...
set nobackup
set nowb
" set noswapfile



"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" => Text, tab and indent related
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" Use spaces instead of tabs
set expandtab

" Be smart when using tabs ;)
set smarttab

" 1 tab == 4 spaces
set shiftwidth=4
set tabstop=4

" Linebreak on 500 characters
set lbr
set tw=500

set ai "Auto indent
set si "Smart indent
set wrap "Wrap lines



""""""""""""""""""""""""""""""
" => Visual mode related
""""""""""""""""""""""""""""""
" Visual mode pressing * or # searches for the current selection
" Super useful! From an idea by Michael Naumann
vnoremap <silent> * :<C-u>call VisualSelection('', '')<CR>/<C-R>=@/<CR><CR>
vnoremap <silent> # :<C-u>call VisualSelection('', '')<CR>?<C-R>=@/<CR><CR>



""""""""""""""""""""""""""""""
" => Status line
""""""""""""""""""""""""""""""
" Always show the status line
set laststatus=2

" " Format the status line
" set statusline=\ %{HasPaste()}%F%m%r%h\ %w\ \ CWD:\ %r%{getcwd()}%h\ \ \ Line:\ %l\ \ Column:\ %c

" 是否打开tabline
let g:airline#extensions#tabline#enabled = 1
let g:airline#extensions#tabline#left_sep = ' '
let g:airline#extensions#tabline#left_alt_sep = '|'
let g:airline#extensions#tabline#formatter = 'default'



"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" => Spell checking
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" Pressing ,sc will toggle and untoggle spell checking
map <leader>sc :setlocal spell!<cr>

" Shortcuts using <leader>
" move to previous spell error
map <leader>sn ]s
" move to next spell error
map <leader>sp [s
" add this word to dictonary
map <leader>sa zg
" show advise list
map <leader>s? z=



"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" => Plugin Config
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" NERDTree
" close vim when it has only nerd tree's window
autocmd bufenter * if (winnr("$") == 1 && exists("b:NERDTreeType") &&b:NERDTreeType == "primary") | q | endif
" use ,ep to show or close nerd tree
map <leader>ep :NERDTreeToggle<CR>

" airline
if !exists('g:airline_symbols')
let g:airline_symbols = {}
endif
let g:airline_left_sep = '>'
let g:airline_left_alt_sep = '>'
let g:airline_right_sep = '<'
let g:airline_right_alt_sep = '<'
let g:airline_symbols.linenr = ','
let g:airline_symbols.branch = '.'

" auto-format
noremap <leader>fm :Autoformat<CR>
let g:autoformat_verbosemode=1
let g:formatdef_xaose = '"clang-format -style=\"{BasedOnStyle: llvm, IndentWidth: 4}\""'
let g:formatters_cpp = ['xaose']
let g:formatters_cs = ['xaose']
let g:formatters_c = ['xaose']
let g:formatters_java = ['xaose']
let g:formatters_shaderlab = ['xaose']

" vim-markdown
au BufRead,BufNewFile *.{md,mdown,mkd,mkdn,markdown,mdwn} set filetype=markdown
let g:vim_markdown_folding_disabled=1

" " vim-markdown-preview
" let vim_markdown_preview_toggle=2
" let vim_markdown_preview_hotkey='<C->'
" let vim_markdown_preview_browser='Mozilla Firefox'

" markdown-preview.vim
map <leader>mp <Plug>StopMarkdownPreview<Plug>MarkdownPreview
map <leader>mpc <Plug>StopMarkdownPreview

" YouCompleteMe
" 配置默认的ycm_extra_conf.py
" let g:ycm_global_ycm_extra_conf = '~/vimfiles/bundle/YouCompleteMe/third_party/ycmd/cpp/ycm/.ycm_extra_conf.py'
let g:ycm_global_ycm_extra_conf = 'D:/Programs/Vim/vimfiles/plugged/YouCompleteMe/leesue/.ycm_extra_conf.py'
" 跳转到定义
map dn :YcmCompleter GoToDefinition<CR>
" 跳转到声明
map dc :YcmCompleter GoToDeclaration<CR>

" https://zhuanlan.zhihu.com/p/33046090
" 配色
highlight PMenu ctermfg=0 ctermbg=242 guifg=black guibg=darkgrey
highlight PMenuSel ctermfg=242 ctermbg=8 guifg=darkgrey guibg=black
" 配置
let g:ycm_add_preview_to_completeopt = 0
let g:ycm_show_diagnostics_ui = 0
let g:ycm_server_log_level = 'info'
let g:ycm_min_num_identifier_candidate_chars = 2
let g:ycm_collect_identifiers_from_comments_and_strings = 1
let g:ycm_complete_in_strings=1
" let g:ycm_key_invoke_completion = '<c-z>'
set completeopt=menu,menuone

noremap <c-z> <NOP>

let g:ycm_semantic_triggers =  {
            \ 'c,cpp,python,java,go,erlang,perl': ['re!\w{2}'],
            \ 'cs,lua,javascript': ['re!\w{2}'],
            \ }
let g:ycm_filetype_whitelist = { 
            \ "c":1,
            \ "cpp":1, 
            \ "objc":1,
            \ "sh":1,
            \ "zsh":1,
            \ "zimbu":1,
            \ }

" " 打开vim时不再询问是否加载ycm_extra_conf.py配置
" let g:ycm_confirm_extra_conf=0
" " 使用ctags生成的tags文件
" let g:ycm_collect_identifiers_from_tag_files = 1
" let g:ycm_cache_omnifunc = 0
" let g:ycm_seed_identifiers_with_syntax = 1
" let g:ycm_min_num_of_chars_for_completion= 2
" let g:ycm_collect_identifiers_from_tags_files = 1
" let g:ycm_collect_identifiers_from_comments_and_strings = 1
" " 诊断窗口
" let g:ycm_always_populate_location_list = 1
"
" " let g:ycm_auto_trigger = 1
" let g:ycm_server_use_vim_stdout = 1
" let g:ycm_server_log_level = 'debug'
"  " YouCompleteMe 功能
" let g:ycm_global_ycm_extra_conf = '~/vimfiles/bundle/YouCompleteMe/Neo/.ycm_extra_conf.py'
" " 补全功能在注释中同样有效
" let g:ycm_complete_in_comments=1
" " 允许 vim 加载 .ycm_extra_conf.py 文件，不再提示
" let g:ycm_confirm_extra_conf=0
" " 开启 YCM 基于标签引擎
" let g:ycm_collect_identifiers_from_tags_files=1
" 引入 C++ 标准库tags，这个没有也没关系，只要.ycm_extra_conf.py文件中指定了正确的标准库路径  
" set tags+=/data/misc/software/misc./vim/stdcpp.tags
" " YCM 集成 OmniCppComplete 补全引擎，设置其快捷键
" inoremap <leader>; <C-x><C-o>
" " 补全内容不以分割子窗口形式出现，只显示补全列表
" set completeopt-=preview
" " 从第一个键入字符就开始罗列匹配项
" let g:ycm_min_num_of_chars_for_completion=1
" " 禁止缓存匹配项，每次都重新生成匹配项
" let g:ycm_cache_omnifunc=0
" " 语法关键字补全
" let g:ycm_seed_identifiers_with_syntax=1
" " 修改对C函数的补全快捷键，默认是CTRL + space，修改为ALT + ;
" let g:ycm_key_invoke_completion = '<M-/>'
" " 设置转到定义处的快捷键为ALT + G，这个功能非常赞
" nmap <M-g> :YcmCompleter GoToDefinitionElseDeclaration <C-R>=expand("<cword>")<CR><CR>



"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" => Helper functions
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
function! VisualSelection(direction, extra_filter) range
    let l:saved_reg = @"
    execute "normal! vgvy"

    let l:pattern = escape(@", "\\/.*'$^~[]")
    let l:pattern = substitute(l:pattern, "\n$", "", "")

    if a:direction == 'gv'
        call CmdLine("Ack '" . l:pattern . "' " )
    elseif a:direction == 'replace'
        call CmdLine("%s" . '/'. l:pattern . '/')
    endif

    let @/ = l:pattern
    let @" = l:saved_reg
endfunction

" Delete trailing white space on save, useful for some filetypes ;)
fun! CleanExtraSpaces()
    let save_cursor = getpos(".")
    let old_query = getreg('/')
    silent! %s/\s\+$//e
    call setpos('.', save_cursor)
    call setreg('/', old_query)
endfun

" Returns true if paste mode is enabled
function! HasPaste()
    if &paste
        return 'PASTE MODE  '
    endif
    return ''
endfunction

" Don't close window, when deleting a buffer
command! Bclose call <SID>BufcloseCloseIt()
function! <SID>BufcloseCloseIt()
   let l:currentBufNum = bufnr("%")
   let l:alternateBufNum = bufnr("#")

   if buflisted(l:alternateBufNum)
     buffer #
   else
     bnext
   endif

   if bufnr("%") == l:currentBufNum
     new
   endif

   if buflisted(l:currentBufNum)
     execute("bdelete! ".l:currentBufNum)
   endif
endfunction

function! CmdLine(str)
    exe "menu Foo.Bar :" . a:str
    emenu Foo.Bar
    unmenu Foo
endfunction
```

