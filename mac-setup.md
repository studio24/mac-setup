# Mac setup for all staff

The following is our standard Mac setup for all staff. The support team are on hand to help you, to get in touch with them either use Slack or call them on 44 (0)1223 328017.

- [Management tools](#management-tools)
- [Mac boxes](#mac-boxes)
- [1 - Initial boot](#1-initial-boot)
- [2 - Support team setup](#2-support-team-setup)
- [3 - Check for system updates](#3-check-for-system-updates)
- [4 - Automatically downloading software](#4-automatically-downloading-software)
- [5 - Setting up essential software](#5-setting-up-essential-software)
  - [Email](#email)
  - [1Password](#1password)
  - [Slack](#slack)
- [6 - Mac user passwords](#6-mac-user-passwords)
- [7 - Setting up other software](#7-setting-up-other-software)
  - [Finder](#finder)
  - [ESET endpoint security](#eset-endpoint-security)
  - [Web-based tools](#web-based-tools)
- [8 - Further setup](#8-further-setup)

## Management tools

This process uses the following platforms to manage automated deployment:

* [Apple Business Manager](https://business.apple.com/) is the central portal for setting up and managing Mac computers, Apple IDs and other devices for Studio 24 and any App Store software licences.
* [Addigy](https://prod.addigy.com/) manages the policies used for deploying common settings and software to Studio 24 computers. It also allows for centralised reporting, management and software deployment.

### Device setup

All Mac systems purchased via the Apple Business account are automatically added to this process. Other MacOS and iOS systems can be added via serial or order number via the Apple Business Manager. Systems that are auto enrolled to this service will automatically download the agent and deploy according to the policy attached to them. Systems purchased from elsewhere will not be automatically enrolled.

## Mac boxes

Please keep the Mac box (including the packing box) and store this in the Cambridge office. 

## 1) Initial boot

* Boot up the new machine
* Select 'Get Started'
* Select you location/region
* Select Accessibility option or 'Not now' to setup later
* Connect to Wi-Fi
    * If you are in the office, connect to `FBC-Tenant` (ask a team member to help with login credentials, see 1Password under "Allia Guildhall Studio 24 WiFi")
* Confirm Addigy/Studio 24 management by selecting 'Enrol'
* Select continue
* Add the user a standard account (username should be in the format initial + last name, i.e. _sjones_)
* Enable Location Services to set Date/Time
* Select continue
**Note** If prompted please skip Apple Intelligence setup, this will need disabling in System settings. You may need to update your Mac OS before this prompt appears
* If your Mac has Touch ID you can set this up in System Settings > Touch ID & Password.

## 2) Support team setup

At the earliest opportunity, request that the support team create a temporary password for the default admin user. 
You will reset the admin password later on, once you have access to 1Password.

At this point the support team will also carry out the other [required tasks](setup-by-support-team.md).

## 3) Check for system updates

* In System Settings check for any Mac OS updates and install them.
* If prompted please skip Apple Intelligence setup, this will need disabling in System settings. You may need to update your Mac OS before this prompt appears
* Double check that Apple Intelligence is disabled in system settings
* If you already have an existing @studio24.net [Apple ID](apple-id.md) you can sign in now

## 4) Automatically downloading software

> [!NOTE]  
> Please note, we use Apple Business Manager to manage all licenses in the App Store. If you need free or paid software from the App Store please talk to the support team to arrange this.

All of the major software is installed (and updated) automatically by Addigy in the background. Please note, this can take some time and some users have reported it takes up to a day to download all software. You can check progress via [Launchpad](https://support.apple.com/en-us/HT202635) which shows all your apps.

* 1Password (for storing passwords securely)
* Alfred (productivity app)
* Amiko font (our company typeface)
* Google Chrome (web browser)
* Google Drive (team shared files)
* Integrity (link checker)
* Mozilla Firefox (web browser)
* Slack (team chat)
* SonicWall Mobile Connect (VPN)
* Tick (time tracking)

This process also:

* Creates a default admin user (see [Mac user passwords](#6-mac-user-passwords) for additional actions)
* Adds office printer
* Sets up default finder and preferences

## 5) Setting up essential software

In order to set up software on your Mac you first need email, 1Password and Slack so you can store complex, secure passwords and communicate with the team.

### Email

* Open the Mail app
* Select "Other Mail account"
* Ensure your username, email address and password are filled in (the support team can provide this information)
* Ensure the account type is "IMAP" and both incoming and outgoing servers are set as `secure.emailsrvr.com`
* Select the apps you want to use: tick "Mail" and untick "Notes"

Please note if you have a large mailbox it may take a few hours to download your email.

You can setup your email signature once your have intranet access via [Email signature](https://intranet.studio24.net/staff/email-signature). Copy and paste this into your Mail client (Preferences, Signatures).

### 1Password

#### New staff

Once you have email access you should have an invitation to 1Password. If you haven't recieved this please contact Simon or Julie to add your user.

You can read about [getting started with 1Password](https://support.1password.com/explore/team-member/).

#### Existing staff

If you are moving to a new computer and have 1Password set up on your old computer, you can use this to setup 1Password on your new computer.

We recommend you first install [Slack](#slack) and send yourself a 1Password login link via your private Slack channel.

If you sign into Slack for the first time on a new computer, select the "Try entering a workspace URL" option so you can enter your login details.

* Select "Try entering a workspace URL"
* Enter the workspace URL: studio24.slack.com
* Select "Sign-in with a password instead"
* Username: Your email
* Password: See 1Password on your old computer
* Enter your authentication code 

On your old computer you can then:

* Go to: _All Accounts > Set Up Another Device_
* Go to Other options > Get link > Get link
* Send this to yourself via Slack private direct message
* Delete the Slack message once complete

#### Choosing a good 1Password account password

You will have to remember your 1Password account password, the Support team can reset this for you if required. 
We recommend using three random words, separated by spaces or hyphens (1Password calls this a "memorable password"). 

#### 1Password browser extensions

[Install browser extensions](https://support.1password.com/getting-started-browser/) to use 1Password via your web browser to make password entry easy. 

#### Password policy

Once you have access to 1Password please ensure you store all your personal logins to your "Employee" vault in 1Password (this is private to you). 
It is a requirement to set complex, secure passwords for all services. We define complex passwords as a minimum of 15 characters. 
We also recommend using two-factor authentication (2FA) wherever possible. 

#### Emergency kit

You can [download an emergency kit](https://support.1password.com/emergency-kit/) with your key login details. 

Do not store the emergency kit file on your computer, either move this to your personal Google Drive or print and store securely.

#### Disable password saving in your browser

You should store passwords in 1Password and not your web browser for security. Disable password autofill in your web browsers: 

##### Safari
* Settings > AutoFill > untick "Usernames and passwords"

##### Chrome
* Settings > Autofill and passwords > Google Password Manager > Settings
* Disable: Offer to save passwords and passkeys

##### Firefox
* Firefox - Preferences > Privacy & Security > Passwords
* Untick "Ask to save passwords"

### Slack

Once you have email access you should receive an invite to Slack. Existing staff should have set up Slack already (see above).

You can read about [getting started with Slack](https://slack.com/intl/en-gb/help/articles/218080037-Getting-started-for-new-Slack-users).

## 6) Mac user passwords

> [!NOTE]  
> Mac user passwords must be a minimum of 12 characters. We recommend using a memorable password made up of 2-3 words.

To meet our security requirements your normal user does not have admin rights. To perform any admin tasks (e.g. install software) you need to use the admin user.

It's important to reset your admin password and store this in 1Password.

1) Open System Settings > Users & Groups 
2) Select the "admin" user "i" icon
3) Select "Reset" next to Password
4) You'll need to enter your admin login details to authorise this
5) You can then enter your new password
3) Store the new admin password in your Studio 24 employee vault in 1Password (this is your personal, private vault)

You should also reset your password for your normal Mac user. Follow the same steps as above but for your normal Mac user.

## 7) Setting up other software

Other software you'll need to create accounts for include the following. Invitations to create accounts for software and web-based tools will be sent to your email account. 

* [Apple ID](apple-id.md) - if you have a new Apple ID you'll need to have email setup first
* Alfred - if you want to use this open the app to configure it
* Google Drive - open up the app and sign in
* [VPN - SonicWall Mobile Connect](vpn.md) (set this up when you are working at home)
* [Telephone system - 3CX](telephone.md)
* [Microsoft Teams](https://www.microsoft.com/en-us/microsoft-teams/group-chat-software) - some clients use Teams for video calls

### Finder

We recommend you do the following to make Finder more useful:

* Finder preferences > Sidebar > Show Hard discs, Show my user home folder
* Finder preferences > Advanced > Show all filename extensions
* Finder > Show view options (⌘J) > Sort by snap to grid

### ESET endpoint security

This is our anti-virus and security software, which everyone must run on their computers.

You'll be sent an email invititation to download this. If you don't have this, ask the support team. 

The email link will download an installer, which you need to run. 
* Follow all instructions on setup.
* ESET will ask permission to filter network content and add proxy configurations. Allow this.

Once ESET is installed:
* Select the "e" icon in your top menu and "Show ESET Endpoint Security"
* Check the Overview page for any warnings. 
* You may need to do the following:
  * Give Full Disk Access: 
    * Go to System Settings > Privacy & Security > Full Disk Access
    * Tick full disk access for ESET Endpoint Security & ESET real-time file system protection

#### Firewall

To set up the ESET firewall you need to log out of your normal user account and login via the admin account set up on your Mac.
You should have your admin password noted in 1Password.

Once logged in as an admin user:
* Skip the Apple Mac setup options, if these appear
* Select the "e" icon in your top menu and "Show ESET Endpoint Security"
* Go to Protections > Network Access
* Enable the Firewall
* Log out as admin user
* Log back in as your normal user

### Web-based tools

Web-based tools you'll need to create accounts for are:

* [Basecamp](https://3.basecamp.com/3091560/) (project management) 
* [Google](https://myaccount.google.com/) 
   * Access [Google Drive shared drives](https://drive.google.com/drive/shared-drives) or via your Finder
   * Access [Google Meet](https://meet.google.com/)
   * Access [Google Calendar](https://calendar.google.com/calendar/u/0/r)
* [Studio 24 intranet](https://intranet.studio24.net/)
* [Tick](https://studio24.tickspot.com/) (time tracking)
  * You can also access Tick via the Tick Mac app 
* [Homerun HR](https://app.homerun.hr/profile) (booking holidays)

Set your default web browser to whichever you are more comfortable with (Firefox, Chrome or Safari).

Tools for PM team and developers:

* [GitHub](https://github.com/studio24/) (project code repository)
* [JIRA](https://studio24.atlassian.net/jira/projects) (task management)
* [Zendesk](https://studio24.zendesk.com/agent/dashboard) (support system - we recommend using Chrome for Zendesk due to compatibility issues in Firefox)

## 8) Further setup

Different team members have further setup instructions:

* [Dev team setup guide](dev-team.md)
* [Design team setup guide](design-team.md)
* [Support team setup guide](support-team.md)
