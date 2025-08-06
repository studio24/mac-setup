# Dev Team setup 

Standard Mac setup for developers at Studio 24.

- [Command Line Tools](#command-line-tools)
- [Homebrew](#homebrew)
- [PHP](#php)
- [Software packages](#software-packages)
- [PhpStorm](#phpstorm)
- [iTerm](#iterm)
- [SSH](#ssh)
- [Git](#git)
- [Oh My Zsh](#oh-my-zsh)
- [Optional software](#optional-software)
- [Local development environment](local-development.md)
- [Configure 1Password for SSH access](1password-ssh.md)

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

You can update packages in Homebrew at any time via:

```bash
brew upgrade
```  

Homebrew will automatically do this when you install new packages that require updates.

## PHP

Install the latest stable version of PHP:

```shell
brew install php
brew install composer
```

Symfony installer:

```shell
brew install symfony-cli/tap/symfony-cli
```

Laravel installer:

```shell
composer global require laravel/installer
```

This installs the following CLI commands:

* `php` - [PHP](https://www.php.net/manual/en/features.commandline.php)
* `composer` - [Composer](https://getcomposer.org/doc/)
* `laravel` - [Laravel CLI](https://laravel.com/docs/12.x)
* `symfony` - [Symfony CLI](https://symfony.com/doc/current/setup.html)

## Software packages

Install following software via Homebrew. Please install packages from Homebrew one-by-one, since they may include setup instructions (e.g. for NVM):

```bash
brew install --cask phpstorm
brew install --cask github
brew install --cask imageoptim
brew install wget
brew install node
brew install nvm
brew install python
brew install pyenv
brew install awscli
brew install nano
brew install goaccess
brew install tableplus
brew install 1password-cli
```

This installs the following CLI commands:

* `aws` - [AWS CLI](https://aws.amazon.com/cli/)
* `nano` - Simple text editor
* `npm` - Node Package Manager
* `nvm` - Node Version Manager
* `op` - [1Password CLI](https://developer.1password.com/docs/cli)
* `python3` and `pip3` for Python 3  
* `wget` - tool to download files
* `goaccess` - tool to analyse access logs. View the [website](https://goaccess.io/) for usage instructions
* `op` - to use 1Password via the cli (for SSH etc)

## PhpStorm

> [!NOTE]  
> The support team will set you up with a JetBrains account based on your studio24.net email address.

1. Open PhpStorm
2. Activate license
3. Log in to JetBrains account (this opens a web browser)
4. Go back to PhpStorm and activate your license

When you set up PHPStorm you can install the following plugins (Settings > Plugins):

* Laravel Idea 
* Symfony Plugin

Restart PHPStorm to activate plugins.

## iTerm

iTerm is a better terminal for the Mac.

```
brew install --cask iterm2
```

## SSH

SSH is used to connect to remote servers, deploy code, and push code to GitHub.

Whenever you need to connect to a remote server please make sure you are on the [VPN](vpn.md).

### SSH key
You should create a new SSH password when you use a new Mac, to help enforce good security.

Create a secure SSH key with a password. Store your SSH key password in your Employee private vault in 1Password.

See instructions on [Generating a new SSH key and adding it to the ssh-agent](https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).

### GitHub

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

### SSH keys for deployment

Add your SSH key to [Studio 24 dev SSH keys repo](https://github.com/studio24/ssh-keys) by following the instructions under "Adding your public key" in the README.

This will give you permission to connect to remote servers. Please note these SSH keys are updated every half an hour on servers.

### SSH aliases

We use a shared [ssh-config](https://github.com/studio24/ssh-config) file to help accessing remote servers.

Install this via:

```
git clone git@github.com:studio24/ssh-config.git ~/.ssh/ssh-config
```

Create a `~/.ssh/config` file and add the following to it:

```
Host *
  UseKeychain yes
  IdentityFile ~/.ssh/id_ed25519

Include ssh-config/*.conf
```

If your SSH private key is not called `id_ed25519`, use the correct name instead.

You can test this by outputting all host shortcuts:

```
~/.ssh/ssh-config/bin/show_hosts
```

You can update your SSH aliases via:

```
git -C ~/.ssh/ssh-config pull
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
git config --global pull.ff only
```

### Studio 24 team

In order to access private repos and push code to any repos you need to be a member of the [Studio 24 team](https://github.com/orgs/studio24/teams/dev-team/members). Request this from the Support Team.

### Global Git ignore file

We use a global [gitignore](https://www.atlassian.com/git/tutorials/saving-changes/gitignore) file to ignore IDE and OS files we don't want to commit to git. Any project files you want
to exclude from git must be added to the project `.gitignore` file. 

Download the global .gitignore file via:

```
curl https://raw.githubusercontent.com/studio24/mac-setup/main/global-gitignore/.gitignore > ~/.gitignore 
```

And tell Git to use it via:

```
git config --global core.excludesfile ~/.gitignore
```

## Oh My Zsh

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

### Theme
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

## Local development environment

To install a local development environment, see the [Local development environment](local-development.md) document.

## Configure 1Password for SSH access

To setup and use 1Password for SSH access to servers, see the [1Password for SSH](1password-ssh.md) document.
