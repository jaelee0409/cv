# cv

```
#### pacman -S mingw-w64-ucrt-x86_64-gcc --noconfirm

#### pacman -S vim git tmux unzip --noconfirm

curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
nvm install node

#### pacman -S mingw-w64-ucrt-x86_64-python mingw-w64-ucrt-x86_64-python-numpy mingw-w64-ucrt-x86_64-python-opencv --noconfirm
```

# Vim
`curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim`
```
set nocompatible
set noswapfile

call plug#begin('~/.vim/plugged')

let mapleader = ","
nmap <leader>nn :NERDTree<cr>

Plug 'scrooloose/nerdtree'
autocmd vimenter * NERDTree

Plug 'scrooloose/syntastic'
Plug 'tpope/vim-commentary'
Plug 'vim-airline/vim-airline'
Plug 'jiangmiao/auto-pairs'
Plug 'valloric/youcompleteme'

call plug#end()

nnoremap <C-S-tab> :tabprevious<CR>
nnoremap <C-tab>   :tabnext<CR>
nnoremap <C-t>     :tabnew<CR>
inoremap <C-S-tab> <Esc>:tabprevious<CR>
inoremap <C-tab>   <Esc>:tabnext<CR>
inoremap <C-t>     <Esc>:tabnew<CR>

nnoremap B ^
nnoremap E $
nnoremap $ <nop>
nnoremap ^ <nop>

syntax enable
set number
set tabstop=4
set shiftwidth=4
set softtabstop=4
set expandtab
set backspace=indent,eol,start
set clipboard=unnamed
set noeb vb t_vb=
set wildmenu
set showmatch
set lazyredraw
set autoread
set incsearch
set hlsearch
nnoremap <leader><space> :nohlsearch<CR>

:set mouse=a
nnoremap <silent> <2-LeftMouse> <LeftMouse>:let @/='\V\<'.escape(expand('<cword'), '\').'\'<cr>:set hls<cr>

colorscheme desert

filetype indent on
```
# Tmux
`vim  ~/.tmux.conf`

```
set-option -g status-position top

# Vim style pane selection
bind h select-pane -L
bind j select-pane -D
bind k select-pane -U
bind l select-pane -R

# Start windows and panes at 1, not 0
set -g base-index 1
set -g pane-base-index 1
set-window-option -g pane-base-index 1
set-option -g renumber-windows on

# Shift Alt vim keys to switch windows
bind -n M-H previous-window
bind -n M-L next-window

# List of plugins
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'

set -g @plugin 'christoomey/vim-tmux-navigator'
set -g @plugin 'dreamsofcode-io/catppuccin-tmux'
set -g @catppuccin_flavour 'mocha'

# Initialize TMUX plugin manager (keep this line at the very bottom of tmux.conf)
run '~/.tmux/plugins/tpm/tpm'

```
