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

## Local development environment

### Privileges

You can use the privileges app to temporarily act as an admin user, you'll need to do this to start MAMP. 

* Open "Privileges" app
* Right-click the icon and select Options > Keep in Dock
* Select "request privileges" to setup this up for the first time

You can now toggle privileges in the dock at any time. Make sure you toggle privileges to open MAMP, you can toggle privileges back after MAMP has opened.

### MAMP Pro

We find MAMP works well for us as a local development environment. If you have advanced requirements we can also use Docker, talk to the Support Team.

1) Download from the website: [MAMP Pro](https://www.mamp.info/en/downloads/)
2) Open the Privileges app and "request privileges" so you are in admin mode
3) Open `MAMP Pro` and register with your personal license code (see 1Password)
4) Select the "Expert view" in MAMP Pro
5) Select "Ports & User" 
6) Set the default ports by selecting "Set ports to 80, 81, 443, 7443, 3306 & 11211" and select "Save"

You can test your MAMP Pro setup by visiting http://localhost/ which should point to `~/Sites/localhost`

#### Add a host
We use a shared local URL for local development websites. Find this in the README of your project in [GitHub](https://github.com/studio24).

It is also recommended to have the project checked out in your local `~/Sites` folder before you add the host in MAMP.

1) Select "Add Host"
2) Select "Empty"
3) Enter your local website URL
4) Choose your local document root, this is normally `public` or `web`
5) Select "Create host"
6) Select "Save" and restart MAMP services

You should now be able to visit your local development URL in a browser. 

By default MAMP creates self-signed SSLs which only work in Chrome and Safari, to get HTTPS working everywhere on your Mac we recommend setting up local SSL as detailed below.

### Local SSL

To get self-signed SSLs working reliably on all web browsers we recommend using [mkcert](https://github.com/FiloSottile/mkcert).

Install via:

```
brew install mkcert
brew install nss
```

To create a locally-trusted development certificate run:

```
mkcert -install
```

You'll need to enter your admin credentials.

Finally, create a local folder to store your self-signed SSL certs:

```
mkdir ~/ssl-certs
```

#### Create a self-signed SSL cert

You can then create self-signed SSL for your local host (in this example the local host URL is `local.host.dev`, change this for the correct local host):

```
cd ~/ssl-certs
mkcert local.host.dev
```

Go into MAMP Pro and update and update your hosts entry to use the new certificate. Under the SSL tab set:

* Certificate file: file ending `*.pem`, e.g. `~/ssl-certs/local.host.dev.pem`
* Cerfificate key file: file ending `*-key.pm`, e.g. `~/ssl-certs/local.host.dev-key.pem`
* Select "Save" to restart services

### PHP

PHP versioning is managed via MAMP Pro. 

#### Setup

In MAMP in the "PHP" section:

* Tick "Activate command line shortcuts for the selected PHP version"
* Tick "Also activate shortcut for Composer"
* Select "Save" to restart services

This installs the following CLI commands (for your current version of PHP):

* `composer` - PHP package manager

#### Switching PHP version

* In MAMP in the "PHP" section select the PHP default version you want to use
* Select "Save" to restart services

If you already have a terminal (or iTerm) window open you can pick up the new PHP version by closing and opening your window, or running:

```
source ~/.profile
```

If you want a version not listed, you can install other PHP versions in MAMP.

### MySQL

#### Setup

In MAMP in the "MySQL" section:

* Tick "Allow network access to MySQL" (this must be only from this Mac)
* Stop MySQL running (stop icon top-right)
* Change your root password to something secure (and store this in your personal vault in 1Password)
* Start the MySQL service

Please note you should be able to set the MySQL connection password for projects in a local file that is **not** committed to git. If you have any issues with this, talk to the Support Team.

**Important note:** It is important to ensure database credentials are not committed to git version control. 

#### Accessing MySQL

You can access MySQL locally via Sequel Ace. 

* Host: 127.0.0.1
* Username: root
* Password: see 1Password for the root password you just set
* Test the connection to ensure this works

#### Migrating Sequel Ace connections
If you want to migrate all of your Sequel Ace DB connections from your old Mac, do the following:

* Open a connection window
* Select all the DB's in the left hand column
* Right Click and select 'export selected'
* Save to a relevant place
* Send to new Macbook via Slack or Google Drive
* Import on new Macbook

**Note:** You will need to re-attach any passwords SSH keys
