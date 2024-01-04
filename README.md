# Guidelines for Access after Migration to the WB Enterprise Account

## Browser Access

Accessing any non-public page on an account migrated to the WB Enterprise Account requires SSO login.
If you are connecting from a WB computer, then the SSO will be automatic.
If you are connecting from a personal computer, then you need to log in using your YubiKey.

SSO login is not required for external collaborators.

## App Access

Accessing repos hosted on the WB Enterprise Account can be accessed in the GitHub app
([iOS app](https://apps.apple.com/us/app/github/id1477376905)/[Android app](https://play.google.com/store/apps/details?id=com.github.android))
after you have logged out and logged in again.
When logging in again you will be asked to authenticate accounts hosted in the Enterprise plan.

On a WB managed smart phone you can just click authenticate and the SSO authentication is automatic.

We are currently working on a solution for personal smart phones.

## Clients

### GitHub Desktop

The first time you push to an account migrated to the WB Enterprise Account using GitHub Desktop,
you will need to log out and log in again in GitHub Desktop.
If you do not do this, you will get an error that you do not have access to that repository.

To do this, go to GitHub Desktop. Then go to `File` -> `Options` -> `Account`.
Select GitHub.com and sign out and then sign in again.
You will then be able to push to the repository.

This does not apply to external collaborators.

### Git Bash/Git CLI

The first time you push to an account migrated to the WB Enterprise Account using Git Bash/Git CLI,
you will need to refresh your credentials.

This does not apply to external collaborators.

#### Windows computer

To do so on a Windows computer, follow these instructions:

1. Search for "Credential Manager" in the Windows menu
2. Look in the "Windows Credentials" tab for the `git:https://github.com` item
3. Expand that item and click "Remove"
4. Go back to Git Bash/Git CLI and run any command that needs authentication. `git push`, `git pull` (on a private repo), etc.
5. Follow the authentication steps.

#### Linux computer

To access your GitHub account,
it will be required to use SSH instead of a username/password combination.
This is because GitHub is phasing out username/password
authentications from Git Bash.

If you are already familiar with SSH keys and have been using them, you can skip to step 4.

1. (optional) Read this article about SSH keys:
[link](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/about-ssh).
2. Run `ls -al ~/.ssh` to check if you already have a valid SSH key set up.
You can find more details and a list of what SSH keys are valid for GitHub
[here](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys).
   - If you do not have a key in a format that GitHub will accept,
   you can create one by following these instructions:
   [link](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).
3. Add the SSH key to your GitHub account by following these instructions:
[link](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account).
4. Authenticate this key to be used on accounts
managed by the WB Enterprise account.
Go to the SSH and GPG key page on your GitHub account:
[link](https://github.com/settings/keys).
   - For the key you want to authenticate in the WB Single Sign-On,
   click the `Configure SSO` button and
   select the account you want to use this key for.
   (Note that you first need to be a member of the account
   for it to appear there).
   - After selecting the account, you need to log in to the WB intranet.
   If you are not using a WB computer (virtual or physical),
   you need to use your YubiKey.
   This step only needs to be done once for each new key.
5. Configure your repository to use SSH instead of HTTPS.
If you are asked for a username/password when accessing a repository,
it means the repository is set to HTTPS.
To switch to SSH, use the following command:
`git remote set-url origin git@github.com:<ACCOUNTNAME>/<REPOSITORY>.git`.
Replace `<ACCOUNTNAME>` with the name
of the WB Enterprise managed GitHub account,
and `<REPOSITORY>` with the name of the repository.
Unfortunately, you need to do this once per repository.

### Access tokens

Access tokens can be used in scripts to
authenticate a GitHub user on Github.com.
However, in order for a token to work on a repo hosted on a
WB Enterprise managed account,
the token needs to be added to the WB Single Sign-On.
Follow these instructions to do so:

1. Go to the access token page on your account: https://github.com/settings/tokens
2. For the token you want to use on the WB Enterprise hosted repo,
click `Configure SSO`.
  - Select the account you want to use this key for.
  (Note that you first need to be a member of the account
  for it to appear there).
  - After selecting the account, you need to log in to the WB intranet.
  If you are not using a WB computer (virtual or physical),
  you need to use your YubiKey.
  This step only needs to be done once for each new key.

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
