# hostname変更
[設定]->[共有]->[コンピュータ名を編集]

# caps lock keyをコマンドキーへ
[設定]->[キーボード]->[修飾キー]->[CapsLockをCommandへ]


# BrewSetup
brew install tmux vim git 
brew install ghq htop ack
brew install thefuck

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

## Font
brew tap caskroom/fonts
brew cask install font-inconsolata
brew cask install font-hack-nerd-font


#エラーとなった、Dockerとの相性か権限設定か
#brew cask install virtualbox

# fisher
brew install fish
echo /usr/local/bin/fish >> /etc/shells
chsh -s /usr/local/bin/fish

## fisherman install
curl -Lo ~/.config/fish/functions/fisher.fish --create-dirs https://git.io/fisher

brew install fzf
fisher z fzf done edc/bass omf/thefuck omf/theme-bobthefish done
fisher install 0rax/fish-bd
fisher edc/bass omf/thefuck omf/theme-bobthefish

### Disable powerline fonts for bobthefish
set -g theme_powerline_fonts no

### Ctrl + g でghqリポジトリの選択が可能に
fisher decors/fish-ghq

# ghq get
ghq get 2ndquadrant-it/barman
ghq get hashicorp/best-practices





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

