# Guidelines for Access after Migration to the WB Enterprise Account

--- 

## SSO authentical on Personal computer/mobiles vs. WB managed computers/mobiles

Any organization GitHub account linked to the WB enterprise account will use what is called SSO when authenticating a user.
What SSO means in practice differ depending on you use a World Bank owned or personal owned computer.
If you are following the instructions below on a World Bank managed device, then SSO is automatic. 
You will be redirected to a page and then automatically redirected back to the page you tried to access.

However, if you are using a personal device, then you will be redirected to the same page, but at that page you will be asked to log in on your World Bank account. 
Typically you will use your Yubikey to log in to your World Bank account. This should be possible to use on most use cases listed below. 
The one use case we know it does not work is on the GitHub mobile app. 
SSO authentication will only work in the app on World Bank owned cell phones.
You can always use the app to access repositories that are not hosted on a World Bank owned account.

---

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

### Access Tokens

Access tokens can be used to authenticate a GitHub user on GitHub.com. There are two types of tokens: classic tokens and fine-grained tokens. 

Classic tokens will eventually be discontinued as fine-grained tokens are considered better practice. However, fine-grained tokens require approval by the account owner. If you know who owns the account for which you are creating the token, you can create a fine-grained token. Otherwise, you can create a classic token as long as they are still allowed.

To create a classic token, visit https://github.com/settings/personal-access-tokens. To create a fine-grained token, visit https://github.com/settings/tokens. Regardless of the type, you will only see the token once after it is created. Make sure to copy it and store it securely, such as in a password manager. GitHub will not be able to show you the token again. If you lose the token, you can always generate a new one. Always make sure to delete the token on GitHub.com if you think there is any risk the token might have been leaked.

When creating the token, you need to do the following two things. There are some differences depending on the type of token you create:
- Assign permission scopes
- Configure WB Single Sign-On (SSO)

#### Permission Scopes

Permission scopes define what the token is allowed to do. If you create a token without permissions, it can only authenticate that it is your token, but it will not authorize any actions, even those you usually have access to. It is considered best practice to grant the least amount of access necessary.

For fine-grained tokens, you select a single organization account for which the token will be valid. Classic tokens can be used for multiple accounts.

Permissions have different names depending on the type of token. For example, if you only need the token for contributing to a repository (e.g., clone, push, pull), you need:
- **Contents** permission for fine-grained tokens
- **Repo** permission for classic tokens

If you need tokens for other purposes, you should review the available permissions.

Note that permissions granted to a classic token apply to all repositories you have access to. This is especially important if you assign broad permissions. If the token is leaked, anyone with the token can perform those actions in your name.

Fine-grained tokens, in contrast, are valid only for a single organization account (or your personal account). Additionally, you can set permissions at the repository level, which is why they are considered more secure.

#### WB Single Sign-On (SSO)

All authentication to GitHub organization accounts within the WB Enterprise subscription by members of those accounts (i.e., not external collaborators) must be configured with WB SSO authentication.

For fine-grained tokens, the token will not be valid until an owner of the organization approves it, unless you are the owner of the account or the token is for your personal account. Once approved, the SSO is configured.

For classic tokens, you can configure SSO yourself after the token is created:
1. Click **Configure SSO** for the token.
2. Select the account you want to use the token for. (You must already be a member of the account for it to appear.)
3. After selecting the account, log in to the WB intranet. If you are not using a WB computer (virtual or physical), you will need to use your YubiKey.


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
