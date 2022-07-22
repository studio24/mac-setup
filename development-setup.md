# Development setup 

Standard Mac setup for developers at Studio 24.

## Terminal

Create Sites folder:

```bash
mkdir ~/Sites
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
brew install --cask iterm2
brew install --cask phpstorm
brew install openssl
brew install wget
brew install node
brew install nvm
brew install ruby
brew install python
brew install composer
brew install deployer
brew install wp-cli
brew install pyenv
```

This installs the following CLI commands:

* `composer` - PHP package manager
* `dep` - Deployer (note: most modern projects use local Deployer loaded via Composer)
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

### Ruby 

If you need to install software via Ruby, the Jekyll docs have a [good guide to installing software locally](https://jekyllrb.com/docs/installation/macos/#install-jekyll) (also requires adding a path to get to your `~/.zshrc` file).

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

Developers should add your SSH key to [Studio 24 dev SSH keys repo](https://github.com/studio24/ssh-keys). This will give you permission to deploy websites.

**Important note:** always use SSH (secure shell) when cloning a git repo, not HTTPS.

### Install global .gitignore file

```bash
curl https://gist.githubusercontent.com/simonrjones/b20e06dfed3b52c8c17b74cda74bcaa7/raw/b78800019c9c0dfdd0f815edacc06fc37e02bad3/.gitignore > ~/.gitignore 
git config --global core.excludesfile ~/.gitignore
```

See https://gist.github.com/simonrjones/b20e06dfed3b52c8c17b74cda74bcaa7

## MAMP

We find MAMP works well for us as a local development environment. If you have advanced requirements we can also use Docker, talk to the Support Team.

Please note: you need the Privileges app to use MAMP Pro, this should be installed via Addigy.

1) Download from the website: [MAMP Pro](https://www.mamp.info/en/downloads/)
2) Open the Privileges app and "request privileges" so you are in admin mode
3) Open "MAMP Pro" and register with your personal license code (see 1Password)

### PHP

PHP versioning is managed via MAMP Pro. When changing PHP version in MAMP Pro either
1. Open a new terminal window and then check the PHP version
```bash
php -v
```
or 
2. Run the below command to pickup the changes and then check the PHP version
```
source = ~/.profile
php -v
```

### Debugging code

* [Debugging a CLI script](https://www.jetbrains.com/help/phpstorm/debugging-a-php-cli-script.html) - you may need to set the working directory to make the CLI script act as intended
* [Debugging an HTTP request](https://www.jetbrains.com/help/phpstorm/debugging-a-php-http-request.html)

### Migrate Sequel Ace connection info
To migrate all of your Sequel Ace DB info.
* Open a connection window
* Select all the DB's in the left hand column
* Right Click and select 'export selected'
* Save to a relevant place
* Send to new Macbook via Slack or Google Drive
* Import on new Macbook
**Note:** You will need to re-attach any passwords SSH keys.

### Apache
Apache is managed via MAMP Pro.

1. Ensure that you enable SSL for local development.
2. Ensure that MAMP is using the correct ports. By default it may be using alternative ones, which will result in connection refused errors unless you manually tag your connections with the correct port numbers.

To use the default ports, click on "Ports & User" on the left navigation, and click the button: 

"Set ports to 80, 81, 443, 7443, 3306 & 11211"

Then save the settings and restart the servers.
3. Note: When upgrading MAMP Pro it may comment out any Additional Parameters within Hosts -> Apache, so be sure to check these are still applied if you run into any problems after updating.
