# Developers Mac setup 

Standard Mac setup for developers at Studio 24.

_Note: this is a work-in-progress and Alan will likely move this into the Mac Setup / Addigy._

## Terminal

Create Sites folder

```bash
mkdir ~/Sites
```

Create Infrastructure folder (Support Team only). 

```bash
mkdir ~/Infrastructure
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
brew upgrade
brew cleanup
```  
## Software packages

Install following packages via Homebrew

Required:
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
Support Team only:
```
brew install direnv
brew install --cask aws-vault
brew install warrensbox/tap/tfswitch
```
Optional:
```bash
brew install --cask paw
brew install --cask textmate
brew install --cask cyberduck
brew install --cask visual-studio-code
brew install --cask sketch
brew install --cask transmit
brew install --cask sublime-text
```
This installs the following extra CLI commands

* `mate` CLI command to open text files in Textmate
* `python3` and `pip3` for Python 3  

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

## PHP

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

### XDebug 3

Edit `php.ini` file for your current version of PHP. View install location of Xdebug via `pecl list xdebug`

Example:

```
zend_extension="/usr/local/Cellar/php@7.4/7.4.14_1/pecl/20190902/xdebug.so"
xdebug.mode=debug
xdebug.client_host=127.0.0.1
xdebug.client_port="9003"
```

Test this works by running `php --version`

XDebug should be listed among the installed extensions.

Next, see instructions on configuring [XDebug in PHPStorm](https://www.jetbrains.com/help/phpstorm/configuring-xdebug.html#integrationWithProduct).

### Debugging code

* [Debugging a CLI script](https://www.jetbrains.com/help/phpstorm/debugging-a-php-cli-script.html) - you may need to set the working directory to make the CLI script act as intended
* [Debugging an HTTP request](https://www.jetbrains.com/help/phpstorm/debugging-a-php-http-request.html)


### MySQL

```bash
brew install mysql@5.7
```

This installs MySQL 5.7 locally, follow the on-screen prompt to run as a service. 

Default username is ```root```

No default password  

To add a password to MySQL and add security run  

```bash
mysql_secure_installation
```
This will prompt for user intervention
```bash
Would you like to setup VALIDATE PASSWORD plugin?
```
Enter ```y```
```bash
Please enter 0 = LOW, 1 = MEDIUM and 2 = STRONG:
```
Enter the required level (0)
Enter a new password when prompted and confirm (rootrogot)

```bash
Do you wish to continue with the password provided?
Remove anonymous users?
Disallow root login remotely?
Remove test database and access to it?
Reload privilege tables now?
```
Enter ```y``` to all of the above prompts  

You should now be able to connect via SQL Ace or the CLI via 

* 127.0.0.1/localhost
* User: root
* Password: rootroot

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
1. Ensure that you enable SSL for local development
2. When upgrading MAMP Pro it may comment out any Additional Paramters within Hosts -> Apache

### PHPStorm

```
brew install --cask phpstorm
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
brew install --cask sketch
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
