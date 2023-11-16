# Notes when testing the demo account in the WB Enterprise account

# Clients

## GitHub Desktop

### WB computer

Works without action: FALSE

**Action needed**: User needs to log out and then log in again to use repos in accounts in the enterprise account


## Git bash

### WB computer

Works without action: FALSE

**Action needed**: User needs to delete the credentials in the credential manager and then pull.

1. Search for "Credential Manager" in the windows menu
2. Look in the "Windows Credentials" tab for the `git:https://github.com` item
3. Expand that item and click "Remove"
4. Go back to git bash and run any command that needs authentication. `git push`, `git pull` (on a private repo), `git clone` etc.

## VSCode

### WB computer
If having Git Bash installed on the computer and choosing that as the terminal in VSCode, then that works given that Git bash has been setup as described above.

## GitKraken

Added GitKraken to approved third-party application: https://github.com/organizations/wbgdemo/settings/oauth_application_policy

### WB computer

Works without action: FALSE

**Action needed**: User needs to log out and then log back in
