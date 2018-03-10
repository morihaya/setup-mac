# hostname変更
[設定]->[共有]->[コンピュータ名を編集]

# BrewSetup
brew install tmux vim git 
brew install ghq

# brew cask
#[caskroom](https://caskroom.github.io/)
brew tap caskroom/cask

brew cask install iterm2 visual-studio-code
brew cask install docker
brew cask install wireshark

#エラーとなった、Dockerとの相性か権限設定か
#brew cask install virtualbox

# fisher
brew install fish
echo /usr/local/bin/fish >> /etc/shells
chsh -s /usr/local/bin/fish

## fisherman install
curl -Lo ~/.config/fish/functions/fisher.fish --create-dirs https://git.io/fisher

brew install fzf
fisher z
fisher fzf


# ghq get
ghq get 2ndquadrant-it/barman
ghq get hashicorp/best-practices





# GitSetup
#[git-aliases](https://githowto.com/aliases)

git config --global alias.co checkout
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.br branch
git config --global alias.hist "log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short"
git config --global alias.type 'cat-file -t'
git config --global alias.dump 'cat-file -p'


# MyGitRepo
cd
mkdir -p go/src/github.com/morihaya/

ln -s /Users/morihaya/go/src/github.com/morihaya myrepo

cd myrepo
git clone git@github.com:morihaya/my-ansible-playbooks.git
git clone git@github.com:morihaya/hoge-go.git

