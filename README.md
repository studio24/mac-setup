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

## Install Xcode CLI tools

Install Xcode Tools

```bash
xcode-select --install
```

### Note with Big Sur

When running `brew update` If you get the error `Error: Your CLT does not support macOS 11` you may need to ensure 

```bash
sudo rm -rf /Library/Developer/CommandLineTools
sudo xcode-select --install
```

## Homebrew

[Install Homebrew](https://brew.sh)

Verify it works.

```bash
brew doctor
```

Update to latest version

```bash
brew update
```

## Git

Setup

```bash
git config --global user.name "Your Name"
git config --global user.email you@example.com
```

Create a secure SSH key with a password. Store your SSH key password in your personal private vault in 1Password.

See instructions on [Generating a new SSH key and adding it to the ssh-agent](https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).

* Copy keys to [GitHub](https://github.com/settings/keys) and [Bitbucket](https://bitbucket.org/account/ssh-keys/)
* Set the key title to your computer name (so you remember where this came from)
* To copy your SSH public key to the clipboard:

```bash
pbcopy < ~/.ssh/id_rsa.pub
```

* Test access to GitHub:

```bash
ssh -T git@github.com
```


If this doesn't work, add the following to `~/.ssh/config`:

```
Host github.com
 Hostname ssh.github.com
 Port 443
```

* Test access to Bitbucket:

```bash
ssh -T git@bitbucket.org
```

Developers should add your SSH key to [Studio 24 dev SSH keys repo](https://bitbucket.org/studio24/ssh-keys). This will give you permission to deploy websites.

**Important note:** always use SSH (secure shell) when cloning a git repo, not HTTPS.

### Install global .gitignore file

```bash
curl https://gist.githubusercontent.com/simonrjones/b20e06dfed3b52c8c17b74cda74bcaa7/raw/b78800019c9c0dfdd0f815edacc06fc37e02bad3/.gitignore > ~/.gitignore 
git config --global core.excludesfile ~/.gitignore
```

See https://gist.github.com/simonrjones/b20e06dfed3b52c8c17b74cda74bcaa7

## Software packages

Install following packages via Homebrew

```bash
brew cask install iterm2
brew cask install paw
brew cask install textmate
brew cask install tableplus
brew cask install docker

brew install wget
brew install node
brew install nvm
brew install ruby
brew install python
brew install composer
brew install deployer
brew install wp-cli
```

This installs the following extra CLI commands

* `mate` CLI command to open text files in Textmate
* `python3` and `pip3` for Python 3

### PHPStorm

```
brew cask install phpstorm
```

When you setup PHPStorm install the following plugins:
* .env files support
* EditorConfig
* Symfony 
* Laravel

Login to your JetBrains account to activate.

### Sketch

If you have a license (front-end team):

```
brew cask install sketch
```

### Ruby setup

Run the following to add the path to ruby in your `~/.zshrc` file:

```
echo 'export PATH="/usr/local/opt/ruby/bin:$PATH"' >> ~/.zshrc
```

If you need to install software via Ruby, the Jekyll docs have a [good guide to installing software locally](https://jekyllrb.com/docs/installation/macos/#install-jekyll) (also requires adding a path to getm to your `~/.zshrc` file).

### NVM setup

```
mkdir ~/.nvm
```

Edit `~/.zshrc` and add:

```
# NVM
export NVM_DIR="$HOME/.nvm"
  [ -s "/usr/local/opt/nvm/nvm.sh" ] && . "/usr/local/opt/nvm/nvm.sh"  # This loads nvm
  [ -s "/usr/local/opt/nvm/etc/bash_completion.d/nvm" ] && . "/usr/local/opt/nvm/etc/bash_completion.d/nvm"  # This loads nvm bash_completion
```
