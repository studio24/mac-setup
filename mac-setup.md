# Mac setup for all staff

The following is our standard Mac setup for all staff. The support team are on hand to help you, to get in touch with them either use Slack or call them on 44 (0)1223 328017.

## Management tools

This process uses the following platforms to manage automated deployment:

* [Apple Business Manager](https://business.apple.com/) is the central portal for setting up and managing Mac computers and other devices for Studio 24 and any App Store software licences.
* [Addigy](https://prod.addigy.com/) manages the policies used for deploying common settings and software to Studio 24 computers. It also allows for centralised reporting, management and software deployment.

### Automated device setup

All Mac systems are automatically added to this process when purchased from Apple. Other MacOS and iOS systems can be added via serial or order number via the Apple Business Manager. Systems that are auto enrolled to this service will automatically download the agent and deploy according to the policy attached to them.

## 1) Boot up your new Mac

* Boot up the new machine
* Select you location/region
* Connect to wi-fi (if you in the office please ask a team member to help you with the login credentials)
* Confirm Addigy/Studio 24 management
* Add the user a standard account (username should be in the format initial + last name, i.e. _sjones_)
* Setup Touch ID
* Choose your look light/dark
* Choose True Tone display yes/no
* Enable Location Services to set Date/Time 

## 2) Automatically downloading software

All of the major software is installed (and updated) automatically by Addigy in the background. Please note, this can take some time and some users have reported it takes up to a day to download all software. You can check progress via [Launchpad](https://support.apple.com/en-us/HT202635) which shows all your apps.

* 1Password 7 (for storing passwords securely)
* Alfred (productivity app)
* Amiko font (our company typeface)
* Google Chrome (web browser)
* Google Drive (team shared files)
* Integrity (link checker)
* Microsoft Office (Word, Excel, Powerpoint)
* Microsoft Teams (online meetings)
* Microsoft To Do (todo app)
* Mozilla Firefox (web browser)
* Sequel Ace (database tool)
* Slack (team chat)
* SonicWall Mobile Connect (VPN)
* Tick (time tracking)
* Zoom (online meetings)

This process also:

* Creates a default admin user (see below for additional actions)
* Adds office printers
* Sets up default finder and preferences

## 3) Setting up software

In order to setup software on your Mac you first need email, 1Password and Slack so you can store complex, secure passwords and communicate with the team.

### Email

* Open the Mail app
* Select Other Mail account
* Ensure your Name, Email Address and Password are filled in (the support team can provide this information)
* On the next screen ensure the account type is IMAP and both incoming and outgoing servere are set as `secure.emailsrvr.com`
* Tick "Mail" and Done
* Select "Protect Mail Activity" and continue

You can setup your email signature once your have intranet access via [Email signature](https://intranet.studio24.net/staff/email-signature). Copy and paste this into your Mail client (Preferences, Signatures).

### 1Password

Once you have email access you should have an invitation to 1Password. If you haven't recieved this please contact Simon or Julie to add your user. You can read about [getting started with 1Password](https://support.1password.com/explore/team-member/).

#### Choosing a good 1Password account password

You will have to remember your 1Password account password, the Support team can reset this for you if required. We recommend using three random words, separated by spaces or hyphens. 

#### Password policy

Once you have access to 1Password please ensure you store all your personal logins to your personal vault in 1Password (this is private to you). It is a requirement to set complex, secure passwords for all services. We define complex passwords as a minimum of 16 characters. We also recommend using two-factor authentication (2FA) wherever possible. 

### Slack

Once you have email access you should receive an invite to Slack. 

You can read about [getting started with Slack](https://slack.com/intl/en-gb/help/articles/218080037-Getting-started-for-new-Slack-users).

### Other software 

Other software you'll need to create accounts for include the following. Invitations to use other software packages will be sent to your email account. 

* Microsoft Office 
* SonicWall Mobile Connect 

### Access to web-based tools

Web-based tools you'll need to create accounts for are:

* [Basecamp](https://3.basecamp.com/3091560/) (project management)
* [Google](https://myaccount.google.com/) (used for Google Drive, Google Meet, Google Calendar)
* [Studio 24 intranet](https://intranet.studio24.net/)
* [Tick](https://studio24.tickspot.com/) (time tracking)
* [Timetastic](https://app.timetastic.co.uk/wallchart) (booking holidays)

Tools for PM team and developers:

* [GitHub](https://github.com/studio24/) (project code repository)
* [JIRA](https://studio24.atlassian.net/jira/projects) (task management)
* [Zendesk](https://studio24.zendesk.com/agent/dashboard) (support system)

## 4) Default admin user

To meet our security requirements your normal user does not have admin rights. To perform any admin tasks (e.g. install software) you need to use the admin user.

At the earliest opportunity, request that the support team change the password for the default admin user. 

You should then:

1) log in as the user 'admin' using this password 
2) Change the password to a new strong passwword
3) Store the new admin password in your personal vault in 1Password

For further information see [User accounts](https://github.com/studio24/handbook-it/blob/Updated-mac-setup/it-guidelines/user-accounts.md).

## 5) Setup steps for Support team

Once a new Mac has passed the intial setup, the support team need to action the following.

These commands are carried out within the [Addigy portal](https://prod.addigy.com):
  
* Setup Device Name via device facts
* Setup asset tag
* Setup Finder & Firmware password via 'Script' deployment

For developers:

* Setup sudo access for your user to install software on the command line

**Note:** Macbooks running the M1 chip do not require a firrmware password as they have an additonal process built in to replace it. 

## 6) For developers

Please also follow the [development setup guide](development-setup.md).

## 7) For designers

* [Figma](https://www.figma.com/)
* [Sketch](https://www.sketch.com/)

## Things to note

### Gatekeeper

When installing programs if you get a message saying the application _"can't be opened because it is from an unidentified developer"_ this is the macOS Gatekeeper program restricting what can be installed.

To manually override this hold **Ctrl** while opening the application, then will then bring up a dialog box where you can select OK to open the application.

See [https://support.apple.com/en-gb/HT202491](https://support.apple.com/en-gb/HT202491)
