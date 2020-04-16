# Developers Mac setup 

Standard Mac setup for developers at Studio 24.

_Note: this is a work-in-progress and Alan will likely move this into the Mac Setup / Addigy._

## Terminal

Update shell (Catalina and above).

```bash
chsh -s /bin/zsh
```

Create Sites folder

```bash
mkdir ~/Sites
```

Install Xcode Tools

```bash
xcode-select --install
```

## Git

[Install Git](https://git-scm.com/download/mac)

Setup

```bash
git config --global user.name "Your Name"
git config --global user.email you@example.com
```

Create a secure SSH key with a password. See [Setup SSH key](https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

Copy keys to [GitHub](https://github.com/settings/keys) and Bitbucket (go to Profile > Settings > SSH keys).

Copy SSH key to clipboard

```bash
pbcopy < ~/.ssh/id_rsa.pub
```

Test access to GitHub

```bash
ssh -T git@github.com
```

Test access to Bitbucket

```bash
ssh -T git@bitbucket.org
```

Add your SSH key to [Studio 24 dev SSH keys repo](https://bitbucket.org/studio24/ssh-keys). This will give you permission to deploy websites.

**Important note:** always use SSH (secure shell) when cloning a git repo, not HTTPS.

### Install global .gitignore file

```bash
curl https://gist.githubusercontent.com/simonrjones/b20e06dfed3b52c8c17b74cda74bcaa7/raw/b78800019c9c0dfdd0f815edacc06fc37e02bad3/.gitignore > ~/.gitignore 
git config --global core.excludesfile ~/.gitignore
```

See https://gist.github.com/simonrjones/b20e06dfed3b52c8c17b74cda74bcaa7

### Troubleshooting SSH access to GitHub

If you get a Connection timed out error when connecting to GitHub via SSH try:

```bash
ssh -T -p 443 git@ssh.github.com
```

If that works, add the following to `~/.ssh/config`

```bash
Host github.com
  Hostname ssh.github.com
  Port 443
```

## Homebrew

[Install Homebrew](https://brew.sh)

Verify it works

```bash
brew doctor
```

Install following packages via Homebrew

```bash
brew cask install iterm2
brew cask install phpstorm
brew cask install transmit
brew cask install textmate
brew cask install github
brew cask install tableplus

brew install wget
brew install node
brew install nvm
brew install python
brew install composer
brew install wp-cli
```

This installs the following extra CLI commands

* `mate` CLI command to open text files in Textmate
* `python3` and `pip3` for Python 3

### NVM setup

```
mkdir ~/.nvm
```

Edit `~/.zshrc` and add:

```
export NVM_DIR="$HOME/.nvm"
  [ -s "/usr/local/opt/nvm/nvm.sh" ] && . "/usr/local/opt/nvm/nvm.sh"  # This loads nvm
  [ -s "/usr/local/opt/nvm/etc/bash_completion.d/nvm" ] && . "/usr/local/opt/nvm/etc/bash_completion.d/nvm"  # This loads nvm bash_completion
```
