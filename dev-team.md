# Dev Team setup 

Standard Mac setup for developers at Studio 24.

## Homebrew

[Install Homebrew](https://brew.sh)

Make sure you run the commands to add Homebrew to your path (the install command tells you what this is).

Verify it works.

```bash
brew doctor
```

If there are any recommendations, it's worth following them.

Update to latest version

```bash
brew update
brew upgrade
brew cleanup
```  

## Software packages

Install following software via Homebrew. Please install packages from Homebrew one-by-one, since they may include setup instructions (e.g. for NVM):

```bash
brew install --cask iterm2
brew install --cask phpstorm
brew install --cask tuple
brew install --cask github
brew install openssl
brew install wget
brew install node
brew install nvm
brew install ruby
brew install python
brew install deployer
brew install wp-cli
brew install pyenv
brew install awscli
brew install nano
```

This installs the following CLI commands:

* `aws` - AWS CLI
* `dep` - Deployer (note: most modern projects use local Deployer loaded via Composer)
* `nano` - Simple text editor
* `npm` - Node Package Manager
* `nvm` - Node Version Manager
* `python3` and `pip3` for Python 3  
* `wget` - tool to download files

### PHPStorm

When you setup PHPStorm install the following plugins:

* .env files support
* EditorConfig
* Symfony 
* Laravel

Login to your JetBrains account to activate.

### Optional software

Optional, install these if you want to use them:

```bash
brew install --cask paw
brew install --cask textmate
brew install --cask cyberduck
brew install --cask visual-studio-code
brew install --cask transmit
brew install --cask sublime-text
```

Textmate installs the following CLI commands:

* `mate` - CLI command to open text files in Textmate

If you have a license (front-end team):

```
brew install --cask sketch
```

## Git

Set default branch to main:

```bash
git config --global init.defaultBranch main
```

User setup: 

```bash
git config --global user.name "Your Name"
git config --global user.email you@example.com
```

Create a secure SSH key with a password. Store your SSH key password in your personal private vault in 1Password.

See instructions on [Generating a new SSH key and adding it to the ssh-agent](https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).

* Copy keys to [GitHub](https://github.com/settings/keys)
* Set the key title to your computer name (so you remember where this came from)
* To copy your SSH public key to the clipboard:

```bash
pbcopy < ~/.ssh/id_ed25519.pub
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

## SSH keys for deployment
Developers need to add your SSH key to [Studio 24 dev SSH keys repo](https://github.com/studio24/ssh-keys). This will give you permission to deploy websites. Please note these SSH keys are updated every half an hour on servers.

**Important note:** always use SSH (secure shell) when cloning a git repo, not HTTPS.

### Install global .gitignore file

```bash
curl https://gist.githubusercontent.com/simonrjones/b20e06dfed3b52c8c17b74cda74bcaa7/raw/b78800019c9c0dfdd0f815edacc06fc37e02bad3/.gitignore > ~/.gitignore 
git config --global core.excludesfile ~/.gitignore
```

See https://gist.github.com/simonrjones/b20e06dfed3b52c8c17b74cda74bcaa7

## Privileges

You can use the privileges app to temporarily act as an admin user, you'll need to do this to start MAMP Pro.

* Open "Privileges" app
* Right-click the icon and select Options > Keep in Dock
* Select "request privileges" to setup this up for the first time

You can now toggle privileges in the dock at any time. Make sure you toggle privileges to open MAMP, you must toggle privileges back after MAMP has opened.

## Local development environment

See [Local development environment](local-development.md)