---
title: "Github Token"
date: 2022-11-26T03:21:05+06:00
draft: false
searchHidden: false

---
# This is a tutorial how to add personal access token from github
This will be done in 2 steps
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
For Linux, you need to configure the local GIT client with a username and email address,
```
git config --global user.name "your_github_username"
```
```
git config --global user.email "your_github_email"
```
```
git config -l
```

Once GIT is configured, we can begin using it to access GitHub. Example:
```
git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY
> Cloning into `YOUR-REPOSITORY`...
Username: <type your username>
Password: <type your password or personal access token (GitHub)
```
Now cache the given record in your computer to remembers the token:
```
git config --global credential.helper cache
```

If needed, anytime you can ```delete``` the cache record by:
```
git config --global --unset credential.helper
```
```
git config --system --unset credential.helper
```
Now try to pull with ```-v``` to verify
```
git pull -v
```



# Thanks 