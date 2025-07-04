# Setup required by the Support Team

These steps are required by the Support Team to help staff setup their Macs.

Once a new Mac has passed the initial setup, the support team need to action the following.

## Everyone
These commands are carried out within the [Addigy portal](https://prod.addigy.com):

* [Setup Device Name via device facts](#setup-device-name-via-device-facts)
* [Setup asset tag](#setup-asset-tag)
* [Setup firmware password via 'Script' deployment](#setup-firmware-password-via-script-deployment)

For developers:
* [Setup sudo access for the user to install software on the command line](#setup-sudo-access---developers-only)

## New staff only
This is carried out for within the [Apple Business Manager portal](https://business.apple.com/):

* Go to Users
* Select Add
* Setup a new user with an Apple ID as user@studio24.net
* Select 'Create Sign-in'
* Select sending the new Sign-in via email

## Addigy setup 

To update these items it is best that the Macbook is online

### Setup Device Name via device facts
* Go to the devices page in the [Addigy portal](https://prod.addigy.com)
* Select the device (click the hyperlinked Device Name)
* Select Scripts
* Select Manage
* Select the script `Change Device Name` & edit
* Update the device name to the correct name eg `Macbook Pro 48`
* Save the script and close the script listing window
* Choose the `Change Device Name` script in the `Run or Assign Script to a device` box
* Select Send
* This should show in the device facts within a few minutes

### Setup asset tag
* Go to the devices page in the [Addigy portal](https://prod.addigy.com)
* Select the device (click the hyperlinked Device Name)
* Select Scripts
* Select Manage
* Select the script `Allocate asset tag` & edit
* Update the device name to the correct name eg `48`
* Save the script and close the script listing window
* Choose the `Allocate asset tag` script in the `Run or Assign Script to a device` box
* Select Send
* This should show in the device facts within a few minutes


### Setup firmware password via 'Script' deployment
* Go to the devices page in Addigy
* Go to the devices page in the [Addigy portal](https://prod.addigy.com)
* Select the device (click the hyperlinked Device Name)
* Select Scripts
* Choose the `Set firmware password` script in the `Run or Assign Script to a device` box
* Select Send
* To check the deployment process select `History` in the device->scripts page

### Setup sudo access - developers only
* Go to the devices page in the [Addigy portal](https://prod.addigy.com)
* Select the device (click the hyperlinked Device Name)
* Select Scripts
* Choose the `Add sudoers file` script in the `Run or Assign Script to a device` box
* Select Send
* To check the deployment process select `History` in the device->scripts page
* Once deployed, connect to the Mac via Liveterminal and run `nano /etc/sudoers.d/username`
* Add the following line to the file (replacing username with the correct username eg `sjones`):
  ```
  username ALL=(ALL) ALL
  ```
* Save the file and exit, exit the LiveTerminal session
* The user should now be able to run commands with sudo access

