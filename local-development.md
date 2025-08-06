# Local development environment setup

> [!NOTE]  
> Please note we no longer use MAMP for local development and have moved to DDEV.

- [Terminal](#terminal)
- [Local SSL](#local-ssl)
- [DDEV](#ddev)
- [Using DDEV](https://github.com/studio24/dev-playbook/blob/main/ddev/using-ddev.md) (dev playbook) 

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

## Local SSL

You may need to install [mkcert](https://github.com/FiloSottile/mkcert) to ensure local SSLs work reliably in Firefox.

```shell
# You'll need to enter your Mac user and password to confirm this 
brew install mkcert nss

# You'll need to enter your admin user and password to confirm this
mkcert -install
```

Restart Firefox once this is done to support local SSLs.

## DDEV

[DDEV](https://ddev.readthedocs.io/en/stable/) is a simple development environment which uses Docker to manage local 
development environments. It's mostly fully automated and allows us to configure software versions (e.g. PHP, MySQL) 
and store these in version control, so everyone uses the same version.

### Installing OrbStack

OrbStack is a fast and simple alternative to Docker Desktop. We have team licenses.

> [!NOTE]  
> Please note if you have Docker Desktop already installed we recommend uninstalling this first.

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

> [!NOTE]  
> To add a member to the Studio 24 Orbstack account admin users can go to the [dashboard](https://orbstack.dev/dashboard), select Studio 24 organisation > Settings > Members > Invite a member.

### Installing DDEV

You must have Docker installed locally first (OrbStack).

To install DDEV, run:

```shell
brew install ddev/ddev/ddev
```

The first time you use DDEV it will ask:

> May we send anonymous DDEV usage statistics and errors?

Answer no.

## Using DDEV

See [Using DDEV in the Dev Playbook](https://github.com/studio24/dev-playbook/blob/main/ddev/using-ddev.md).
