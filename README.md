# Plugins with Vim-Plug
## Installing Neovim
* On Mac
```bash
brew install neovim
```
* Ubuntu
```bash
sudo apt install neovim
```
* Arch
```bash
sudo pacman -S neovim
```
## Create config
Make directory for your Neovim config
```bash
mkdir ~/.config/nvim
```
Create an **init.vim** file
```bash
touch ~/.config/nvim/init.vim
```
## Install vim-plug
```bash
curl -fLo ~/.config/nvim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```
You should now have **plug.vim** in your autoload directory so it will load of on start
## Add a new file for plugins
We will manage our plugins in a separate file for the sake of my own sanity
```bash
mkdir ~/.config/nvim/vim-plug

touch ~/.config/nvim/vim-plug/plugins.vim
```
## Let's add some plugins
Add the following to **~/.config/nvim/vim-plug/plugins.vim**
```bash
" auto-install vim-plug
if empty(glob('~/.config/nvim/autoload/plug.vim'))
  silent !curl -fLo ~/.config/nvim/autoload/plug.vim --create-dirs
    \ https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
  "autocmd VimEnter * PlugInstall
  "autocmd VimEnter * PlugInstall | source $MYVIMRC
endif

call plug#begin('~/.config/nvim/autoload/plugged')

    " Better Syntax Support
    Plug 'sheerun/vim-polyglot'
    " File Explorer
    Plug 'scrooloose/NERDTree'
    " Auto pairs for '(' '[' '{'
    Plug 'jiangmiao/auto-pairs'

call plug#end()
```
## Source your plugins
Add the following line to **init.vim**
```bash
source $HOME/.config/nvim/vim-plug/plugins.vim
```
## Vim-Plug commands
Open **nvim**
```bash
nvim
```
Check the status of your plugins
```bash
:PlugStatus
```
Install all of your plugins
```bash
:PlugInstall
```
To update your plugins
```bash
:PlugUpdate
```
After the update you can press **d** to see the differences or run
```bash
:PlugDiff
```
To remove plugins that are no longer defined in the **plugins.vim** file
```bash
:PlugClean
```
Finally if you want to upgrade vim-plug itself run the following
```bash
:PlugUpgrade
```
