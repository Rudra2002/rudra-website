---
title: "Github Token"
date: 2022-11-26T03:21:05+06:00
draft: false
searchHidden: false
Description: This is a tutorial how to create personal access token from github and configure your github client to use it.
---
# This is a tutorial how to create personal access token from github and configure your github client to use it.
### This will be done in 2 steps:
1. Create a access token.
2. Add the token to your git client.

## Step 1 [Creating github token]:
- Go to your github account settings.
- Go to Developer Setting at the bottom.
- Go to Personal Access token and create a Tokens(classic)
- Fill the information and copy the token
- The token will be like this ```ghp_JCEAUrOjKjdicbjshrv50Dasdfkv```
## Step 2 [Adding the token to your client]

## For Windows:
Go to Credential Manager from Control Panel > Windows Credentials > find git:https://github.com > Edit > On Password replace with with your GitHub Personal Access Token > You are Done.
	
If you don’t find git:https://github.com => Click on Add a generic credential => Internet address will be git:https://github.com and you need to type in your username and password will be your GitHub Personal Access Token => Click Ok and you are Done.
## For Macos
Click on the Spotlight icon (magnifying glass) on the right side of the menu bar. Type Keychain access then press the Enter key to launch the app > In Keychain Access, search for github.com > Find the internet password entry for github.com > Edit or delete the entry accordingly > You are Done.

## For Linux(git)
- For Linux, you need to configure the local GIT client with a username and email address,
for this install the github-cli tool from [install](https://github.com/cli/cli#installation).
- Then check if the cli tool is installed with this command:
```
gh version
```
- Then paste the following command:
```
gh auth login
```
Then choose where you want to store the token
```
➜  ~ gh auth login
? What account do you want to log into?  [Use arrows to move, type to filter]
> GitHub.com
  GitHub Enterprise Server
```
- Then it will ask if you want to configure with ```HTTPS``` or ```SSH```
```
? What is your preferred protocol for Git operations?  [Use arrows to move, type to filter]
> HTTPS
  SSH
```
We will choose HTTPS
- It will ask if we want to authenticate the git.
```
? Authenticate Git with your GitHub credentials? (Y/n)
```
We will type ```Y``` and press enter
- Then we will be asked if we want to authenticate with we browser login or github token. We will choose with token.
```
? How would you like to authenticate GitHub CLI?  [Use arrows to move, type to filter]
  Login with a web browser
> Paste an authentication token
```
- Then paste the token you got from before:
```
? Paste your authentication token: ****************************************
```
- Then it will show you the config is successful.
```
- gh config set -h github.com git_protocol https
✓ Configured git protocol
✓ Logged in as Abxy
```
- After that we need to tell git to use the gh token.
```
gh auth setup-git
```
- Then we need to add our email and username to git.
```
git config --global user.email "you@example.com"
```
```
git config --global user.name "Your Name"
```
Done.
# Thanks 
