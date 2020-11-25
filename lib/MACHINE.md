![0xKakashi](../banner.png)

# 📔 COOKBOOK

> Developer Bookmarks, Resources, References and Guides

---

## 🖥 MACHINE

> Developer Machine Configuration Guide

---

1. [Command Line](#command-line)
2. [Applications](#applications)
3. [Browser](#browser)
4. [Keys](#keys)
5. [Customizations](#customizations)

---

### COMMAND LINE

Install [__Homebrew__](https://brew.sh) Package Manager

```bash
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

Install [__Zsh__] Terminal

```bash
$ brew install zsh
```
_Mac is now using by default ZSH terminal_

Install [__Oh My Zsh__] Terminal Environment

```bash
# curl
$ sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Initialize [__Homebrew Cask__](https://docs.brew.sh) Application Manager

```bash
$ brew cask
```

Install [__Homebrew Packages__](https://formulae.brew.sh/formula)

```bash
# archey - machine logger
$ brew install archey

# git - version control
$ brew install git

# gnupg - encryption keys
$ brew install gnupg

# gh - github cli
$ brew install gh

# ipfs - interplanetary file system
$ brew install ipfs

# node - node.js v8 engine
$ brew install node

# tree - directory prompt
$ brew install tree

# wget - http interaction cli
$ brew install wget

# yarn - node package manager
$ brew install yarn
```

Install [__NPM Global Packages__](https://npmjs.com)

```bash
# serverless - serverless framework
$ npm i -g serverless

# ganache-cli - truffle suite ganache cli interaction
$ npm i -g ganache-cli
```

---

### APPLICATIONS

__Apple App Store__

* [BitWarden]()
* [Affinity Design]()
* [Affinity Photo]()
* [CleanMyMac X]()
* [Magnet]()
* [TweetDeck]()
* [Telegram]()
* [Xcode]()
* [Developer]()
* [SF Symbols]()

__Brew Cask__

```bash
# authy

# ipfs-desktop

# ganache
```

__Download__

* [Ableton]()
* [Discord]()
* [Figma]()

---

### BROWSER

__Extensions__

---

### KEYS

__GitHub__

__AWS__

---

### CUSTOMIZATIONS

__$ROOT__

```
.Trash
.archey-ip
.aws/
.cache/
.cocoapods/
.gitconfig
.gnupg/
.ipfs/
.ipfs-desktop/
.node-gyp/
.npm/
.npmrc
.nuxtrc
.oh-my-zsh/
.serverless/
.serverlessrc
.ssh/
.vim/
.viminfo
.vscode/
.wget-hsts
.yarn/
.yarnrc
.zshrc
Applications/
Desktop/
Documents/
Library/
Movies/
Music/
Pictures/
Public/
Users/
```

__`~/.zshrc`__

```
# initialize
export ZSH="/Users/AlexanderSmith/.oh-my-zsh"
ZSH_THEME=spaceship
export UPDATE_ZSH_DAYS=7

# plugins
plugins=(
  git,
  npm
)

source $ZSH/oh-my-zsh.sh

# tabtab actions
[[ -f ~/.config/tabtab/__tabtab.zsh ]] && . ~/.config/tabtab/__tabtab.zsh || true

# start-up
archey
```
