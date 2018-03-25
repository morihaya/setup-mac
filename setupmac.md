# hostname変更
[設定]->[共有]->[コンピュータ名を編集]

# caps lock keyをコマンドキーへ
[設定]->[キーボード]->[修飾キー]->[CapsLockをCommandへ]

# ズーム機能を有効
[設定]->[アクセシビリティ]->[ズーム機能]->[キーボードショートカットを使ってズーム]

# BrewSetup
brew install tmux vim git 
brew install ghq htop ack pstree
brew install thefuck terraform

## install python
brew install python
cd ~/Downloads/
wget https://bootstrap.pypa.io/get-pip.py
sudo python get-pip.py

# brew cask
#[caskroom](https://caskroom.github.io/)
brew tap caskroom/cask

brew cask install iterm2 visual-studio-code
brew cask install docker
brew cask install wireshark
brew cask install macdown
brew cask install macpass

## Need password
brew cask install onedrive

## Window manupilate
brew cask install shiftit
[設定]->[セキュリティとプライバシー]->[アクセシビリティ]->[プライバシー]->[ShiftFitを追加]

# Font
brew tap caskroom/fonts
brew cask install font-inconsolata
brew cask install font-hack-nerd-font

## iterm2のフォントを変更
[preference]->[profile]->[text]->[change font]->"Knack Regular Nerd Font Complete"

#エラーとなった、Dockerとの相性か権限設定か
#brew cask install virtualbox

# vim
## install plugin manager
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim

curl -fLo ~/.local/share/nvim/site/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim


string trim "
call plug#begin('~/.vim/plugged')

Plug 'vim-airline/vim-airline'
Plug 'tpope/vim-fugitive'
Plug 'scrooloose/nerdtree'
Plug 'Xuyuanp/nerdtree-git-plugin'

call plug#end()

map <C-n> :NERDTreeToggle<CR>
" ~/.vimrc

ln -s ~/.vimrc ~/.config/nvim/init.vim


# fisher
brew install fish
echo /usr/local/bin/fish >> /etc/shells
chsh -s /usr/local/bin/fish

## fisherman install
curl -Lo ~/.config/fish/functions/fisher.fish --create-dirs https://git.io/fisher

brew install fzf
fisher z fzf done edc/bass omf/thefuck omf/theme-bobthefish done 0rax/fish-bd  edc/bass omf/thefuck omf/theme-bobthefish

## Disable powerline fonts & enable nerd for bobthefish
set -g theme_powerline_fonts no
set -g theme_nerd_fonts yes

## Ctrl + g でghqリポジトリの選択が可能に
fisher decors/fish-ghq

## enable docker completion for fish
wget https://raw.githubusercontent.com/docker/cli/master/contrib/completion/fish/docker.fish -O ~/.config/fish/completions/docker.fish

# ghq get sample
ghq get 2ndquadrant-it/barman
ghq get hashicorp/best-practices

## embulk & digdag
brew cask install caskroom/versions/java8
brew install embulk digdag

### digファイルをyamlハイライト有効
echo "autocmd BufRead,BufNewFile *.dig set filetype=yaml" >> ~/.vimrc

# GitSetup
## aliases
#[git-aliases](https://githowto.com/aliases)

git config --global alias.co checkout
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.br branch
git config --global alias.hist "log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short"
git config --global alias.type 'cat-file -t'
git config --global alias.dump 'cat-file -p'

## Use ssh only push
[ここのコメント](https://qiita.com/yshz/items/e72d92813350be5728ef)
git config --global 'url.git@github.com:.pushinsteadof' 'https://github.com/'


# MyGitRepo
cd
mkdir -p go/src/github.com/morihaya/

ln -s /Users/morihaya/go/src/github.com/morihaya myrepo

cd myrepo
git clone git@github.com:morihaya/my-ansible-playbooks.git
git clone git@github.com:morihaya/hoge-go.git


# terraform
brew install terraform

# Visual Studio Code
## basicaly setting
    "terminal.external.osxExec": "iterm.app",
    "terminal.integrated.fontFamily": "Knack Nerd Font"

## Install plugin
+ VSCode extension for Ansible

# nodejs
#VSCode extension for Ansible1でremote shell機能を使うためにNodeJSが必要だった
brew install nvm

# golang
brew install go
sudo mkdir -m 775 /usr/local/go
sudo chown $USER:admin /usr/local/go
echo "set -x GOPATH /usr/local/go" >> ~/.config/fish/config.fish
git config --global ghq.root $GOPATH/src

## すでにghqでpackageをインストールしていた場合は以下を行う
cp -p ~/.ghq/* $GOPATH/src

## VSC extentionでdockerを使った検証を行うためのマウント許可
[docker]->[Preference]->[File Sharing]->[+]->[command + shift + G]->[/usr/local/go/src/]を追加->[Apply & Restart]

# tmux
brew install reattach-to-user-namespace


string trim '
setw -g mode-keys vi

set-option -g default-command "exec reattach-to-user-namespace -l $SHELL"
bind-key    -T copy-mode-vi v     send-keys -X begin-selection
bind-key    -T copy-mode-vi y     send-keys -X copy-pipe-and-cancel "reattach-to-user-namespace pbcopy"
bind-key    -T copy-mode-vi Enter send-keys -X copy-pipe-and-cancel "reattach-to-user-namespace pbcopy"
' > ~/.tmux.conf





