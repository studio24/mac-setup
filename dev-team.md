# Dev Team setup 

Standard Mac setup for developers at Studio 24.

## Command Line Tools

You may need to re-install these when upgrading to a new OS version (you need to run this after upgrading to macOS Ventura). Toggle privileges (so you have admin rights) and run the following in terminal:

```
xcode-select --install
```

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
brew install --cask phpstorm
brew install --cask tuple
brew install --cask github
brew install --cask imageoptim
brew install --cask 1password/tap/1password-cli
brew install openssl
brew install wget
brew install node
brew install nvm
brew install ruby
brew install python
brew install wp-cli
brew install pyenv
brew install awscli
brew install nano
brew install goaccess
brew install symfony-cli/tap/symfony-cli
```

This installs the following CLI commands:

* `aws` - [AWS CLI](https://aws.amazon.com/cli/)
* `nano` - Simple text editor
* `npm` - Node Package Manager
* `nvm` - Node Version Manager
* `op` - [1Password CLI](https://developer.1password.com/docs/cli)
* `python3` and `pip3` for Python 3  
* `symfony` - [Symfony CLI](https://symfony.com/download)
* `wget` - tool to download files
* `wp` - [WP CLI](https://wp-cli.org/)
* `goaccess` - tool to analyse access logs. View the [website](https://goaccess.io/) for usage instructions

## iTerm 

iTerm is a better terminal for the Mac.

```
brew install --cask iterm2
```

### Oh My Zsh

We use [Oh My Zsh](https://github.com/ohmyzsh/ohmyzsh/wiki) to customise your terminal, install via:

```
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

We use two plugins:

* [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting/blob/master/INSTALL.md#oh-my-zsh)
* [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions/blob/master/INSTALL.md#oh-my-zsh)

Install these via:

```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

Edit your `~/.zshrc` file:

```
nano ~/.zshrc
```

Add the plugins to the list of plugins for Oh My Zsh to load:

```
plugins=( 
    # other plugins...
    zsh-syntax-highlighting zsh-autosuggestions
)
```

Close and re-open iTerm to enable the new plugins.

#### Theme
You can also use different [themes](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes) if you wish. The team prefer the 
`agnoster` theme, which you need to install a Powerline font to use. You can do this via:

```
git clone --depth 1 git@github.com:powerline/fonts.git ~/fonts
cd ~/fonts
./install.sh
cd ../
rm -Rf fonts
```

Update your `~/.zshrc` file:

```
ZSH_THEME="agnoster"
```

You then need to select a Powerline font in iTerm (Preferences > Profile > Text). `Noto Mono for Powerline` is recommended.

## PHPStorm

When you setup PHPStorm install the following plugins:

* .env files support
* EditorConfig
* Symfony 
* Laravel

Login to your JetBrains account to activate.

## Optional software

Optional, install these if you want to use them:

```bash
brew install --cask rapidapi
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

### Studio 24 team

In order to access private repos and push code to any repos you need to be a member of the [Studio 24 team](https://github.com/orgs/studio24/teams/dev-team/members). Request this from the Support Team.

### Global Git ignore file

We use a global [gitignore](https://www.atlassian.com/git/tutorials/saving-changes/gitignore) file to ignore IDE and OS files we don't want to commit to git. Any project files you want
to exclude from git must be added to the project `.gitignore` file. 

Install the global .gitignore file via:

```bash
curl https://raw.github.com/studio24/mac-setup/blob/main/global-gitignore/.gitignore > ~/.gitignore 
git config --global core.excludesfile ~/.gitignore
```

## SSH

Whenever you need to connect to a remote server please make sure you are on the [VPN](vpn.md).

### SSH keys for deployment
Developers need to add your SSH key to [Studio 24 dev SSH keys repo](https://github.com/studio24/ssh-keys). This will give you permission to deploy websites. Please note these SSH keys are updated every half an hour on servers.

**Important note:** always use SSH (secure shell) when cloning a git repo, not HTTPS.

### SSH aliases

We use a shared [ssh-config](https://github.com/studio24/ssh-config) file to help accessing remote servers.

Install this via:

```
git clone git@github.com:studio24/ssh-config.git ~/.ssh/ssh-config
```

Create a `~/.ssh/config` file and add the following to it. 

```
Host *
	UseKeychain yes
	IdentityFile ~/.ssh/id_rsa

Include ssh-config/*.conf
```

If your ssh key is not called `id_rsa`, use the correct name instead.

You can test this by outputting all host shortcuts:

```
~/.ssh/ssh-config/bin/show_hosts
```

## Privileges

You can use the privileges app to temporarily act as an admin user, you'll need to do this to start MAMP Pro.

* Open "Privileges" app
* Right-click the icon and select Options > Keep in Dock
* Select "request privileges" to setup this up for the first time

You can now toggle privileges in the dock at any time. Make sure you toggle privileges to open MAMP, you must toggle privileges back after MAMP has opened.

## Local development environment

To install PHP, Composer and MySQL, see the [Local development environment](local-development.md) document.
