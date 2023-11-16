# Notes when testing the demo account in the WB Enterprise account

## Client

### GitHub Desktop

#### WB computer - member

Works without action: FALSE

**Action needed**: User needs to log out and then log in again to use repos in accounts in the enterprise account

#### WB computer - external

Works without action: TRUE

### Git bash

#### WB computer

Works without action: FALSE

**Action needed**: User needs to delete the credentials in the credential manager and then pull.

1. Search for "Credential Manager" in the windows menu
2. Look in the "Windows Credentials" tab for the `git:https://github.com` item
3. Expand that item and click "Remove"
4. Go back to git bash and run any command that needs authentication. `git push`, `git pull` (on a private repo), `git clone` etc.

### VSCode

#### WB computer
If having Git Bash installed on the computer and choosing that as the terminal in VSCode, then that works given that Git bash has been setup as described above.

### GitKraken

Added GitKraken to approved third-party application: https://github.com/organizations/wbgdemo/settings/oauth_application_policy

#### WB computer

Works without action: FALSE

**Action needed**: User needs to log out and then log back in

## Settings

### Repo creation

> Members will be able to create only selected repository types. Outside collaborators can never create repositories.

We want to be in control of the repos to be created on our account. So we would like to be able to disable the possibility for members to create repos of all types.

Currently this is set on enterprise level that members can create public and private repos but not internal repos. We think this should be up to each account owner.

### Delete and transfer repos
> Allow members to delete or transfer repositories for this organization
If enabled, members with admin permissions for the repository will be able to delete or transfer public and private repositories. If disabled, only organization owners can delete or transfer repositories.

This is enabled on the enterprise level. We would like to disable this option as we do not want the risk that a team member by accident (or maliciously) transfer away or delete a repo.
