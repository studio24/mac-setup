# Local development environment setup

> [!NOTE]  
> Please note we no longer use MAMP for local development and have moved to DDEV.

## Terminal

Create Sites folder:

```shell
mkdir ~/Sites
```

You should clone all projects into this folder, using SSH to clone from GitHub since this uses SSH keys to authenticate 
with GitHub. As an example, to clone this repo you'd use: 

```shell
git clone git@github.com:studio24/mac-setup.git
```

## DDEV

[DDEV](https://ddev.readthedocs.io/en/stable/) is a simple development environment which uses Docker to manage local 
development environments. It's mostly fully automated and allows us to configure software versions (e.g. PHP, MySQL) 
and store these in version control, so everyone uses the same version.

### Installing OrbStack

OrbStack is a fast and simple alternative to Docker Desktop. We have team licenses.

_Please note if you have Docker Desktop already installed we recommend uninstalling this first._

Installation instructions:

* Login to the [OrbStack website](https://orbstack.dev/) in your default web browser using your GitHub account
* Install the app via `brew install orbstack`
* Open OrbStack to configure it
    * Select Docker to use Docker containers
* Sign in to OrbStack to use the professional license (sign in button bottom-left or Account > Sign in)
* Open OrbStack Settings
    * In General tick Automatically download updates
  * If you want OrbStack to automatically start on login, tick Start at login

OrbStack should prompt when it needs updating (you'll need your Mac admin password to update software).

_Note: to add a member to the Studio 24 Orbstack account admin users can go to the [dashboard](https://orbstack.dev/dashboard), 
select Studio 24 organisation > Settings > Members > Invite a member._

### Installing DDEV

You must have Docker installed locally first (OrbStack).

To install DDEV, run:

```shell
brew install ddev/ddev/ddev
```

The first time you use DDEV it will ask:

> May we send anonymous DDEV usage statistics and errors?

Answer no.

## Upgrading DDEV

```shell
brew upgrade ddev/ddev/ddev
```

## Using DDEV

To start DDEV run:

```shell
ddev start
```

To view the website in your default browser:

```shell
ddev launch
```

To list all current projects:

```shell
ddev list
```

To restart DDEV (for example if config has changed) run:

```shell
ddev restart
```

To stop DDEV run

```shell
ddev stop
```

You can also shut down all DDEV projects via:

```shell
ddev poweroff
```

### Mailpit

By default all emails sent from your website are captured in a tool called Mailpit, which allows you to review emails sent by the website.

To open Mailpit run:

```shell
ddev mailpit
```

### Using a database

To access the database via TablePlus:

```shell
ddev tableplus
```

Import a database via an SQL file:

```shell
ddev import-db < [filename]
```

Export SQL files for a database:

```shell
ddev export-db
```

### Xdebug

Xdebug comes with it by default. To enable Xdebug run:

```shell
ddev xdebug on
```

To disable Xdebug:

```shell
ddev xdebug off
```

To toggle Xdebug on and off:

```shell
ddev xdebug toggle
```

Read instructions on [how to setup Xdebug in PHPstorm and VSCode](https://ddev.readthedocs.io/en/stable/users/debugging-profiling/step-debugging/).

### Running commands in DDEV
All commands must be run via ddev to ensure you are using the correct version of PHP. For example:

```shell
ddev composer install
```

Some [useful commands](https://ddev.readthedocs.io/en/stable/users/usage/cli/#lots-of-other-commands) from the DDEV docs:

* `ddev composer` gives access to Composer
* `ddev artisan` (Laravel only) gives direct access to the Laravel artisan CLI
* `ddev console` (Symfony only) gives access to the Symfony console CLI
* `ddev craft` (Craft CMS only) gives access to the Craft CLI
* `ddev npm` gives direct access to the npm CLI
* `ddev wp` (WordPress) give direct access to the WP CLI
* `ddev ssh` takes you into the web container
* `ddev exec [command]` executes a command inside the web container
