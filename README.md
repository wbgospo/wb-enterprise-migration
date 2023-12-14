# Guidelines for Access after Migration to the WB Enterprise Account

## Browser Access

Accessing any non-public page on an account migrated to the WB Enterprise Account requires SSO login. 
If you are connecting from a WB computer, then the SSO will be automatic. 
If you are connecting from a personal computer, then you need to log in using your YubiKey.

SSO login is not required for external collaborators.

## Clients

### GitHub Desktop

The first time you push to an account migrated to the WB Enterprise Account using GitHub Desktop,
you will need to log out and log in again in GitHub Desktop. 
If you do not do this, you will get an error that you do not have access to that repository.

To do this, go to GitHub Desktop. Then go to `File` -> `Options` - `Account`.
Select GitHub.com and sign out and then sign in again.
You will then be able to push to the repository.

This does not apply to external collaborators.

### Git Bash/Git CLI

The first time you push to an account migrated to the WB Enterprise Account using Git Bash/Git CLI,
you will need to refresh your credentials.

To do so on a Windows computer, follow these instructions:

1. Search for "Credential Manager" in the Windows menu
2. Look in the "Windows Credentials" tab for the `git:https://github.com` item
3. Expand that item and click "Remove"
4. Go back to Git Bash/Git CLI and run any command that needs authentication. `git push`, `git pull` (on a private repo), etc.
5. Follow the authentication steps.

This does not apply to external collaborators.

### VSCode, RStudio, and other IDEs using Git Bash/Git CLI

The first time you push to an account migrated to the WB Enterprise Account using an IDE that uses Git Bash/Git CLI,
you will need to follow the instructions in the Git Bash/Git CLI section above.

This does not apply to external collaborators.

### GitKraken

The first time you push to an account migrated to the WB Enterprise Account using GitKraken,
you will, similarly to GitHub Desktop, log out and log in again in GitKraken.

To do so, go to `File` -> `Preferences` -> `Integration` -> `GitHub` and then click `Disconnect`. 
Then log in again.

This does not apply to external collaborators.
