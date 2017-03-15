---
layout: post
title:  Configuring Vim
---

## 1. Making Vim Prettier
These are some of the settings to configure Vim to make it look prettier. And then wget atom-dark-256.vim

Inside your .vim directory make a folder named 'colors'
{% highlight ruby %}
cd ~/.vim
mkdir colors
cd colors
wget https://raw.githubusercontent.com/gosukiwi/vim-atom-dark/master/colors/atom-dark-256.vim
#if you do ls you should see the newly installed file
{% endhighlight %}


## 2. Your .vimrc file
Copy and paste this into your ~/.vimrc file
{% highlight ruby %}

set nocompatible                                                 "We want the
set clipboard=unnamedplus
set autochdir
set tags=./tags,tags;$HOME

so ~/.vim/plugins.vim

noremap % v%


syntax enable


set backspace=indent,eol,start                                    
let mapleader = ',' 						  
set nonumber							  
set noerrorbells visualbell t_vb=                                 
set tabstop=8
set autowriteall
set expandtab
set softtabstop=4
set shiftwidth=4


"-----------------Visuals-------------------"

colorscheme atom-dark-256

set t_CO=256

"We will fake a custom left padding for each window.
highlight LineNr  ctermbg=bg

set foldcolumn=2

hi foldcolumn ctermbg=bg


"Get rid of ugly split borders
hi vertsplit ctermfg=bg ctermbg=bg


"----------------Split Management------------"

set splitbelow
set splitright

nmap <C-J> <C-W><C-J>
nmap <C-K> <C-W><C-K>
nmap <C-H> <C-W><C-H>
nmap <C-L> <C-W><C-L>



"-----------------Mappings-------------------"
set hlsearch
set incsearch




"-----------------Mappings-------------------"

"Make it easy to edit the .vimrc file"
nmap <leader>ev :tabedit ~/.vimrc<cr>

"Make it easy to edit the snippets file
nmap <leader>es :e ~/.vim/snippets/<cr>

nmap <leader>eu :e ~/.vim/Ultisnips/<cr>



"Add simple highlight removal"
nmap <leader><space> :nohlsearch<cr>


nmap <leader>f :tag<space>

"Reload snippets file"
nmap <leader>ras ::call ReloadAllSnippets()<cr>


"Echo the current files' name"
nmap <leader><leader>n :echo expand('%:p')<cr>


"-----------------Plugins-------------------"


"/
"/ CtrlP
"/
let g:ctrlp_custom_ignore = 'node_modules\|git'
let g:ctrlp_match_window = 'top,order:ttb,min:1,max:30,results:30'


"/
"/ NERDTree
"/
let NERDTreeHijackNetrw = 0


"Make NERDTree easier to toggle"
nmap <c-T> :NERDTreeToggle<cr>
nmap <c-F12> :CtrlPBufTag<cr>
nmap <c-E> :CtrlPMRUFiles<cr>


"/
"/ Greplace.vim
"/

set grepprg=ag                "We want to use A for search

let g:grep_cmd_opts = '--line-numbers --noheading'



"/
"/ Greplace.Vim
"/
set grepprg=ag        "We want to use Ag for the search"

let g:grep_cmd_opts = '--line-numbers --noheading'


"/
"/ pdv
"/
let g:pdv_template_dir = $HOME ."/.vim/bundle/pdv/templates_snip"
nnoremap <leader>d :call pdv#DocumentWithSnip()<cr>


"/
"/ Ultisnips
"/
let g:UltiSnipsSnippetsDir= '~/.vim/UltiSnips/'
let g:UltiSnipsExpandTrigger="<tab>"
let g:UltiSnipsJumpForwardTrigger="<tab>"
let g:UltiSnipsJumpBackwardTrigger="<s-tab>"

"-------------------Laravel specific-----------"
"-----routes file--- "
nmap <leader>lr :e /home/blackstone/Code/sar-upgrade/app/Http/routes.php<cr> 

"-------------got the website routes file--------------------"
nmap <leader>srw :e /home/blackstone/Code/sar-upgrade/app/Http/routes/website.php<cr>

nmap <leader><leader>c :CtrlP /home/blackstone/Code/sar-upgrade/app/Http/Controllers<cr>

nmap <leader><leader>p :CtrlP<cr>app/Http/Controllers/PagesController<cr><c-F12>eventsS<cr>

"-------Models-------------
nmap <leader><leader>m :CtrlP<cr>/home/blackstone/Code/sar-upgrade/app/Models/<cr>

"----------Views-----------"
nmap <leader><leader>v :e /home/blackstone/Code/sar-upgrade/resources/views/<cr>


nmap <leader><leader>c :e /home/pranayaryal/Code/blog/app/Http/Controllers/<cr>







"-------------------Auto Commands------------"

"Automatically source Vimrc file on save"

augroup autosourcing
        autocmd!
        autocmd BufWritePost .vimrc source %
augroup END



"------------------Arrange the imported files in order of length------------"
vmap <leader>su ! awk '{ print length(), $0 \| "sort -n \| cut -d\\  -f2-" }'<cr>



function! IPhpInsertUse()
        call PhpInsertUse()
            call feedkeys('a',  'n')
endfunction
autocmd FileType php inoremap <leader>n <Esc>:call IPhpInsertUse()<CR>
autocmd FileType php noremap <leader>n :call PhpInsertUse()<CR>

function! IPhpExpandClass()
        call PhpExpandClass()
            call feedkeys('a', 'n')
endfunction
autocmd FileType php inoremap <leader>nf <Esc>:call IPhpExpandClass()<CR>
autocmd FileType php noremap <leader>nf :call PhpExpandClass()<CR>

"Notes and Tips
" - Press 'zz' 	to instantnly center the line where the cursor is located

{% endhighlight %}

## 4. Install Vundle which is a package manager for installing vim plugins
{% highlight ruby %}
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
{% endhighlight %}

## 5. Make a file inside ~/.vim named plugins.vim
{% highlight ruby %}
cd ~/.vim
touch plugins.vim
{% endhighlight %}


## 6. Your ~/.vim/plugins.vim file
Type this inside your plugins.vim file
{% highlight ruby %}
sudo vim ~/.vim/plugins.vim
{% endhighlight %}

Paste this code there
{% highlight ruby %}
filetype off                  " required

" set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/Vundle.vim

call vundle#begin()

Plugin 'VundleVim/Vundle.vim'

Plugin 'tpope/vim-vinegar'

Plugin 'scrooloose/nerdtree'

Plugin 'ctrlpvim/ctrlp.vim'

Plugin 'rking/ag.vim'

Plugin 'skwp/greplace.vim'

Plugin 'tpope/vim-surround'

Plugin 'StanAngeloff/php.vim'

Plugin 'arnaud-lb/vim-php-namespace'

Plugin 'honza/vim-snippets'

Plugin 'tobyS/vmustache'

Plugin 'tobyS/pdv'

Plugin 'SirVer/ultisnips'

Plugin 'scrooloose/nerdcommenter'

Plugin 'tpope/vim-fugitive'

Plugin 'Valloric/YouCompleteMe'

Plugin 'terryma/vim-multiple-cursors'

"Python syntax stuff
Plugin 'nvie/vim-flake8'
Plugin 'vim-scripts/Pydiction'
Plugin 'vim-scripts/indentpython.vim'
Plugin 'scrooloose/syntastic'


"code folding
Plugin 'tmhedberg/SimpylFold'


"Colors
Plugin 'altercation/vim-colors-solarized'
Plugin 'jnurmine/Zenburn'
Plugin 'sjl/badwolf'

" All of your Plugins must be added before the following line
call vundle#end()            " required

filetype plugin indent on    " required
" To ignore plugin indent changes, instead use:
"filetype plugin on
"
" Brief help
" :PluginList       - lists configured plugins
" :PluginInstall    - installs plugins; append `!` to update or just :PluginUpdate
" :PluginSearch foo - searches for foo; append `!` to refresh local cache
" :PluginClean      - confirms removal of unused plugins; append `!` to auto-approve removal
"
" see :h vundle for more details or wiki for FAQ
" Put your non-Plugin stuff after this line

{% endhighlight %}

Then type ,ev to go into your .vimrc file and then type
{% highlight ruby %}
:PluginInstall
{% endhighlight %}

This should install all your plugins

## 6. Download ctags
Then type this in the project you want to be searchable. You might have to create a tags/ directory in your project
{% highlight ruby %}
ctags -R
{% endhighlight %}

I hope this helps
