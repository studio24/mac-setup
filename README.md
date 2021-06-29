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
brew upgrade
brew cleanup
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

```bash
brew install php
brew install php@7.3
brew install php@7.4
brew install brew-php-switcher
```

Install required PHP modules:

```bash
pecl install xdebug
```

To switch to PHP 7.4 use:

```bash
brew-php-switcher 7.4
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

## Software packages

Install following packages via Homebrew

```bash
brew install --cask iterm2
brew install --cask paw
brew install --cask textmate
brew install --cask tableplus
brew install --cask cyberduck
brew install --cask docker


brew install openssl
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

### Apache

Edit the Apache configuration file:

```
sudo nano /etc/apache2/httpd.conf
```

Find the following line:

```
#Include /private/etc/apache2/extra/httpd-vhosts.conf
```

Below it, add the following line:

```
Include /private/etc/apache2/vhosts/*.conf
```

This configures Apache to include all files ending in `.conf` in the `/private/etc/apache2/vhosts/` directory. Now we need to create this directory.

```
mkdir /etc/apache2/vhosts
cd /etc/apache2/vhosts
```

We can then create a new file eg

```sudo nano studio24.conf```

Then add the details for the host

```
<VirtualHost *:80>
        DocumentRoot "/Users/sjones/Sites/studio24/web"
        ServerName local.studio24.net
        ErrorLog "/private/var/log/apache2/local.studio24.net-error_log"
        CustomLog "/private/var/log/apache2/local.studio24.net-access_log" common

        <Directory "/Users/sjones/Sites/studio24/web">
            AllowOverride All
            Require all granted
        </Directory>
</VirtualHost>
```

Check the Apache config

```
sudo apachectl configtest
```

(Re)start the Apache service

```
sudo apachectl restart
```

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
