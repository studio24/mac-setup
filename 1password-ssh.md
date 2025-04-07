# 1Password for SSH

We can use 1Password for SSH key management and storage.

[1Password documentation for the SSH agent](https://developer.1password.com/docs/ssh/agent/)

## 1Password settings
These settings are correct for version 8.10.70 


### Developer tab 
* Tick 'Use the SSH agent'
* Tick 'Integrate with 1Password CLI'
Under advanced 
* Select 'Ask for approval for each new: application and terminal session'
* Select 'Remember key approval: until 1Password locks'
* Tick 'Display key names when authorizing connections'
* Select 'Open SSH URLs with: iTerm2'

### SSH Config 
Add the code below to your ```~/.ssh/config``` file

```
Host *
        IdentityAgent "~/Library/Group Containers/2BUA8C4S2C.com.1password/t/agent.sock"
```
