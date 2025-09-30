# Setting up Proton VPN

We use Proton VPN for dedicated IP connectivity software to a secure network. This is essential for deployments 
and access to some IP protected websites (e.g. staging sites). This requires the Support team creating your user on the 
Proton business account.

> [!IMPORTANT]  
> You must connect to the VPN when you are not in the office or on your home network. 

## Installation
This is installed by default to all devices via Addigy as part of the initial Mac setup. 

## Setup
1. Open the app, this can be found via Alfred by searching for `ProtonVPN`
2. Select Signin with SSO 
   1. You will be prompted for your Proton login credentials (via Google).

3. If prompted to use a new network extension select “Open System Settings”, this should open the correct window, if not open `System Settings -> General -> Login items and extensions` then go to `Extensions -> Network extensions`
   1. Toggle ProtonVPN to “On” 
   2. Authenticate with your admin user account
   3. Select "Done"
   3. On the welcome screen select “Continue”
4. Once Proton VPN is open select `Profiles -> Create profile`
   1. Select a name for the profile eg “Work” 
   2. Select Feature - Standard 
   3. Select Country - OFFICE-VPN 
   4. Select server - OFFICE-VPN#1 
   5. Select VPN Protocol - Smart 
   6. Save
5. Select Proton VPN -> Settings 
   On the General tab toggle on 
   1. Start on boot 
   2. Start minimized 
   3. System notifications

6. On the Connection tab 
   1. Select Auto connect - Disabled 
   2. Select Quick Connect - Work (this is the name set in the initial profile setup)
   3. Select Protocol - Smart   
   4. Toggle VPN Accelerator on 
   5. Toggle LAN connections on

You can now close the preferences window.

7. Upon first run you will be prompted that “ProtonVPN would like to Add VPN Configurations”, select Allow

## Usage
1. Open the app, this can be found via Alfred by searching for `prtotonvpn`
   or
2. In the application bar
3. Select quick connect (this should now be configured for to connect t the correct server) or select the `OFFICE-VPN` connection and `connect`







