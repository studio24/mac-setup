# Local development environment setup

## Terminal

Create Sites folder:

```bash
mkdir ~/Sites
```

You should clone all projects into this folder, using SSH to clone from GitHub since this uses SSH keys to authenticate 
with GitHub. As an example, to clone this repo you'd use: `git clone git@github.com:studio24/mac-setup.git`

## MAMP Pro

We find MAMP works well for us as a local development environment. If you have advanced requirements we can also use 
[Docker](https://www.docker.com/), talk to the Support Team.

### Installing MAMP

1) Download from the website: [MAMP Pro](https://www.mamp.info/en/downloads/)
2) Open the Privileges app and "request privileges" so you are in admin mode
3) Open `MAMP Pro` and register with your personal license code (see 1Password)
4) Select the "Expert view" in MAMP Pro
5) Select "Ports & User"
6) Set the default ports by selecting "Set ports to 80, 81, 443, 7443, 3306 & 11211" and select "Save"

You can test your MAMP Pro setup by visiting http://localhost/ which should point to `~/Sites/localhost`

### Add a host
We use a shared local URL for local development websites. Find this in the README of your project in [GitHub](https://github.com/studio24).

It is also recommended to have the project checked out in your local `~/Sites` folder before you add the host in MAMP.

1) Select "Add Host"
2) Select "Empty"
3) Enter your local website URL. We use the `local` subdomain for local sites with the same TLD as the production URL, e.g. `local.studio24.net`.
4) Choose your local document root, this is normally `public` or `web`
6) Select "Create host"
7) Select "Save" and restart MAMP services

You should now be able to visit your local development URL in a browser.

By default MAMP creates self-signed SSLs which only work in Chrome and Safari, to get HTTPS working everywhere on your Mac we recommend setting up local SSL as detailed below.

### Opening MAMP

In normal usage you need to do the following to open MAMP securely:

1) In the `Privileges` app "request privileges" so you are in admin mode
2) Open `MAMP Pro` 
4) In the `Privileges` app "remove privileges" so you are in standard mode

## Local SSL

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

### Create a self-signed SSL cert

You can then create self-signed SSL for your local host (in this example the local host URL is `local.host.dev`, change this for the correct local host):

```
cd ~/ssl-certs
mkcert local.host.dev
```

Go into MAMP Pro and update your hosts entry to use the new certificate. Under the SSL tab set:

* Certificate file: file ending `*.pem`, e.g. `~/ssl-certs/local.host.dev.pem`
* Cerfificate key file: file ending `*-key.pm`, e.g. `~/ssl-certs/local.host.dev-key.pem`
* Select "Save" to restart services

## PHP

PHP versioning is managed via MAMP Pro.

### Setup

In MAMP in the "PHP" section:

* Click the "+" next to the PHP version and install the PHP version you need to you have it available. MAMP will restart when you install the new version.
* Tick "Activate command line shortcuts for the selected PHP version"
* Tick "Also activate shortcut for Composer"
* Under "What to log" ensure "All errors and warnings (E_ALL)" is selected
* Under "Log errors" tick "to screen" to output local errors to screen
* Select "Save" to restart services

This makes the following CLI commands available (for your current version of PHP):

* `composer` - PHP package manager
* `php` 

### Switching PHP version

* In MAMP in the "PHP" section select the PHP default version you want to use
* Select "Save" to restart services

If you already have a terminal (or iTerm) window open you can pick up the new PHP version by closing and opening your window, or running:

```
source ~/.profile
```

If you want a version not listed, you can install other PHP versions in MAMP.

## MySQL

Please note MAMP uses MySQL 5.7, if you require a more modern version you will need to use Docker.

### Setup

In MAMP in the "MySQL" section:

* Tick "Allow network access to MySQL" (this must be only from this Mac)
* Stop MySQL running (stop icon top-right)
* Change your root password to something secure (and store this in your personal vault in 1Password)
* Start the MySQL service

Please note you should be able to set the MySQL connection password for projects in a local file that is **not** committed to git. If you have any issues with this, talk to the Support Team.

**Important note:** It is important to ensure database credentials are not committed to git version control.

### Accessing MySQL

You can access MySQL locally via Table Plus.

* Host: `127.0.0.1`
* Username: `root`
* Password: see 1Password for the root password you just set
* Test the connection to ensure this works

When creating new databases it's recommended to select the encoding: `UTF-8 Unicode (utf8mb4)`

### Using MySQL on the command line

Edit your `~/.zshrc` file:

```
export PATH="/Applications/MAMP/Library/bin:${PATH}"
```

This makes the following CLI commands available:

* `mysql` and other [MySQL utilities](https://dev.mysql.com/doc/refman/5.7/en/programs-client.html)

### Migrating Sequel Ace connections
If you want to migrate all of your Sequel Ace DB connections from your old Mac, do the following:

* Open a connection window
* Select all the DB's in the left hand column
* Right Click and select 'export selected'
* Save to a relevant place
* Send to new Macbook via Slack or Google Drive
* Import on new Macbook

**Note:** You will need to re-attach any SSH keys when accessing MySQL over SSH.

### Migrating from Sequal Ace to TablePlus
As of April 2024 [we are migrating away](https://3.basecamp.com/3091560/buckets/10590409/documents/7260701423) from using Sequel Ace to TablePlus for connecting to databases.

You will need to download the latest version of TablePlus from the [TablePlus website](https://tableplus.com/download), and follow the instructions in the Basecamp message.

