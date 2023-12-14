# Guidelines for Access after Migration to the WB Enterprise account

## Browser access

Accessing any non-public page on an account migrated to the WB Enterprise requires SSO log in. 
If you are connecting from a WB computer, then the SSO will be automatic. 
If you are connecting from a personal computer, then you need to log in using your YubiKey.

SSO log-in is not required for external collaborators.

## Clients

### GitHub Desktop

The first time you push to an account migrated to the WB Enterprise account using GitHub Desktop,
you will need to log out and log in again in GitHub Desktop. 
If you do not do this, you will get an error that you do not have access to that repository.

To do this, go to GitHub desktop. Then go to `File` -> `Options` - `Account`.
Select GitHub.com and sign out and then sign in again.
You will then be able to push to the repository.

This does not apply to external users.

### Git bash/Git CLI

The first time you push to an account migrated to the WB Enterprise account using Git bash/Git CLI,
you will need to refresh your credentials.

To do so on a Windows computer, follow these instructions:

1. Search for "Credential Manager" in the windows menu
2. Look in the "Windows Credentials" tab for the `git:https://github.com` item
3. Expand that item and click "Remove"
4. Go back to Git bash/Git CLI and run any command that needs authentication. `git push`, `git pull` (on a private repo), etc.
5. Follow the authentication steps.

This does not apply to external users.

### VSCode, RStudio and other IDEs using Git bash/Git CLI

The first time you push to an account migrated to the WB Enterprise account using an IDE that uses Git bash/Git CLI,
you will need to follow the instructions in the Git bash/Git CLI section above.

This does not apply to external users.

### GitKraken

The first time you push to an account migrated to the WB Enterprise account using GitKraken,
you will, similarly to GitHub Desktop log out and log in again in GitKraken.

To do so, go to `File` -> `Preferences` -> `Integration` -> `GitHub` and then click `Disconnect`. 
Then log in again.

