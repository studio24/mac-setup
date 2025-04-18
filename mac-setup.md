# Mac setup for all staff

The following is our standard Mac setup for all staff. The support team are on hand to help you, to get in touch with them either use Slack or call them on 44 (0)1223 328017.

## Management tools

This process uses the following platforms to manage automated deployment:

* [Apple Business Manager](https://business.apple.com/) is the central portal for setting up and managing Mac computers, Apple IDs and other devices for Studio 24 and any App Store software licences.
* [Addigy](https://prod.addigy.com/) manages the policies used for deploying common settings and software to Studio 24 computers. It also allows for centralised reporting, management and software deployment.

### Device setup

All Mac systems purchased via the Apple Business account are automatically added to this process. Other MacOS and iOS systems can be added via serial or order number via the Apple Business Manager. Systems that are auto enrolled to this service will automatically download the agent and deploy according to the policy attached to them. Systems purchased from elsewhere will not be automatically enrolled.

### Mac boxes

Please keep the Mac box (including the packing box), store this in the Cambridge office if possible. 

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

## 2) Default admin user

To meet our security requirements your normal user does not have admin rights. To perform any admin tasks (e.g. install software) you need to use the admin user.

At the earliest opportunity, request that the support team create a temporary password for the default admin user.

You should then:

1) log in as the user "admin" using this temporary password
2) Change the password to a new complex password
3) Store the new admin password in your personal vault in 1Password

You'll need to [login to 1Password via a web browser](https://studio24.1password.com/) to store the new admin password. To do this you'll need:

* Your email address
* [Your secret key](https://support.1password.com/secret-key/)
* Your 1Password account password

If you have an existing computer you can access this via the "Set up another device" page.

If this if your first computer we recommend using your Emergency Kit from 1Password.

## 3) Check for system updates
* In System Settings check for any Mac OS updates and install them.
* If prompted please skip Apple Intelligence setup, this will need disabling in System settings. You may need to update your Mac OS before this prompt appears
* Double check that Apple Intelligence is disabled in system settings

## 4) Automatically downloading software

All of the major software is installed (and updated) automatically by Addigy in the background. Please note, this can take some time and some users have reported it takes up to a day to download all software. You can check progress via [Launchpad](https://support.apple.com/en-us/HT202635) which shows all your apps.

* 1Password 7 (for storing passwords securely)
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

* Creates a default admin user (see below for additional actions)
* Adds office printer
* Sets up default finder and preferences

## 5) Setting up essential software

In order to setup software on your Mac you first need email, 1Password and Slack so you can store complex, secure passwords and communicate with the team.

### Email

* Open the Mail app
* Select "Other Mail account"
* Ensure your username, email address and password are filled in (the support team can provide this information)
* Ensure the account type is "IMAP" and both incoming and outgoing servere are set as `secure.emailsrvr.com`
* Select the apps you want to use: tick "Mail" and untick "Notes"
* Select "Protect Mail activity" and continue

You can setup your email signature once your have intranet access via [Email signature](https://intranet.studio24.net/staff/email-signature). Copy and paste this into your Mail client (Preferences, Signatures).

### 1Password

Once you have email access you should have an invitation to 1Password. If you haven't recieved this please contact Simon or Julie to add your user. 

If you have an existing computer you can use this to setup 1Password on your new computer. Go to: _Accounts > Studio 24 > Set up another device_. You can scan a setup code or send yourself a link via email. 

If you need to enter the account details the sign-in address is: `studio24.1password.com`

You can read about [getting started with 1Password](https://support.1password.com/explore/team-member/).

#### Choosing a good 1Password account password

You will have to remember your 1Password account password, the Support team can reset this for you if required. We recommend using three random words, separated by spaces or hyphens. 

#### 1Password browser extensions

[Install browser extensions](https://support.1password.com/getting-started-browser/) to use 1Password via your web browser to make password entry easy. 

#### Password policy

Once you have access to 1Password please ensure you store all your personal logins to your personal vault in 1Password (this is private to you). It is a requirement to set complex, secure passwords for all services. We define complex passwords as a minimum of 15 characters. We also recommend using two-factor authentication (2FA) wherever possible. 

#### Emergency kit

You can [download an emergency kit](https://support.1password.com/emergency-kit/) with your key login details. 

Do not store the emergency kit file on your computer, either move this to your personal Google Drive or print and store securely.

#### Disable password saving in your browser

You should store passwords in 1Password and not your web browser for security. 

* Safari - Settings > AutoFill > untick "Usernames and passwords"
* Firefox - Preferences > Privacy & Security > untick "Ask to save logins and passwords for websites"
* Chrome - Settings > Auto-fill > Passwords > untick "Offer to save passwords"

### Slack

Once you have email access you should receive an invite to Slack. 

You can read about [getting started with Slack](https://slack.com/intl/en-gb/help/articles/218080037-Getting-started-for-new-Slack-users).



## 6) Setting up other software 

Other software you'll need to create accounts for include the following. Invitations to create accounts for software and web-based tools will be sent to your email account. 

* Alfred - if you want to use this open the app to configure it
* Google Drive - open up the app and sign in
* [VPN - SonicWall Mobile Connect](vpn.md) 
* [Telephone system - 3CX](telephone.md)
* [Apple ID](apple-id.md) - when you receive an email invitation

### Finder

We recommend you fo the following to make Finder more useful:

* Finder preferences > Sidebar > Show Hard discs, Show my user home folder
* Finder preferences > Advanced > Show all filename extensions
* Finder > Show view options > Sort by snap to grid

### ESET endpoint security

This is our anti-virus and security software, which everyone needs to run on their computers.

You'll be sent an email invititation to download this. Follow all instructions on setup.

You can remove ESET from the dock via:

* Go to ESET > Preferences
* Go to Preferences > User > Interface
* Untick "Present application in Dock"

### Access to web-based tools

Web-based tools you'll need to create accounts for are:

* [Basecamp](https://3.basecamp.com/3091560/) (project management)
* [Google](https://myaccount.google.com/) (used for Google Drive, Google Meet, Google Calendar)
* [Studio 24 intranet](https://intranet.studio24.net/)
* [Tick](https://studio24.tickspot.com/) (time tracking)
* [Timetastic](https://app.timetastic.co.uk/wallchart) (booking holidays)

Set your default web browser to whichever you are more comfortable with (Firefox, Chrome or Safari).

Tools for PM team and developers:

* [GitHub](https://github.com/studio24/) (project code repository)
* [JIRA](https://studio24.atlassian.net/jira/projects) (task management)
* [Zendesk](https://studio24.zendesk.com/agent/dashboard) (support system - please note we have issues accessing Zendesk in Firefox)

## 7) Setup steps for Support team

Once a new Mac has passed the initial setup, the support team need to action the following.

These commands are carried out within the [Addigy portal](https://prod.addigy.com):
  
* Setup Device Name via device facts
* Setup asset tag
* Setup firmware password via 'Script' deployment

This is carried out within the [Apple Business Manager portal](https://business.apple.com/):

* Setup a new Apple ID as user@studio24.net
* Select 'Create Sign-in'
* Select sending the new Sign-in via email

For developers:

* Setup sudo access for the user to install software on the command line

## 8) Further setup

Different team members have further setup instructions:

* [Dev team setup guide](dev-team.md)
* [Design team setup guide](design-team.md)
* [Support team setup guide](support-team.md)
