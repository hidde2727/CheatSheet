# Git

## Assumptions
It is assumed your terminal is inside your git project folder, or you ran
```shell
cd /path/to/project/folder
```
{} will be used for values you need to choose/fill in yourself. **They cannot contain whitespace**

## Initializing a repository

#### From a local project:
First create a GitHub project <br>
<ins>!!! The GitHub project must be EMPTY !!!</ins> (No ReadMe/.gitignore) <br>
Then from the terminal inside your local project:
```shell
git remote add origin https://github.com/{YourUsername}/{YourProjectName}.git
git push
```
You can replace origin with another remote name (but then need to replace origin in all the other commands configuring remotes too)

#### From an existing GitHub project:
First navigate to the folder where you want to place the repository, then:
```shell
# Note that this will create a folder with the name YourProjectName
git clone https://github.com/{YourUsername}/{YourProjectName}.git
```

## Setting your git information
**Please note that setting your git username and email will expose both to the internet** (If you are also using GitHub) <br>
So please use only your first name and use the [GitHub private email](https://docs.github.com/en/account-and-profile/how-tos/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/setting-your-commit-email-address)<br> 
The private email will look something like: 93196280+hidde2727@users.noreply.github.com
```shell
git config --global user.name "Your name"
git config --global user.email "Your email"
```

## Commiting
To commit to the **<ins>current branch</ins>** you are on use:
```shell
# Add your current changes:
git add .
# Or if you want to add individual files:
git add ./path/to/certain/file
# Commit them locally
git commit -m "Your commit message"
# Push the local changes to your remotes (for example to GitHub)
git push
```

## Branches
#### Change current branch
To change the current branch that you are on use:
```shell
git checkout {branchname}
```
**Make sure to first commit changes before using checkout**: files may else be deleted
#### Create branch
To create a branch that branches from the current branch you are on use:
```shell
git branch {your new branch name}
# You probably want to start using the branch as well:
git checkout {your new branch name}
# Use this command to publish the branch to your remotes (for example to GitHub):
git push -u origin {your new branch name}
```
#### Merging branches
After a while you probably want to merge your changes back into another branch <br>
You can either use the local GIT, or you can use GitHub <br>
Please <ins>make sure you commited all the changes</ins> you made beforehand
###### With local git
```shell
# Switch to the branch that will receive the merge
git checkout {your receiving branch name}
# Make sure the branch is up to date
git pull
# Merge (make sure it creates a commit message with --no-ff)
git merge --no-ff {branch name to merge}
# Optionally delete the branch that was merged
git branch -d {branch name to merge}
# Keep your remotes (for example GitHub) up-to-date
git push
```
###### With GitHub (my preferred method)
On your repository page, go to "Pull Requests" and click "New pull request"<br>
There you can specify which branch you want to merge into another (Notice the arrow, please don't merge the wrong way)<br>
After you have created the pull request GitHub will check if there are merge conflicts<br>
If there are no merge conflicts you will receive a button to merge the two branches <br>
If there are merge conflicts GitHub will help you resolve them

## Staying up-to-date
#### Pull
Use the following command if your remote (for example GitHub) has changes that you don't have locally
```shell
git pull
```
Under the hood this will first call ```git fetch``` and then merge the remote with your local version
#### Push
Use the following command if your remote (for example GitHub) doesn't have changes that you have locally
```shell
git push
```

## GitHub auth
To access private repositories/push to repositories you need to authenticate yourself for GitHub.
If you are using vscode it will do it for you, but sometimes this doesn't work.
To use git in vscode, without letting vscode manage your git credentials, first disable vscodes management:
Settings > 'Search git auth' > disable both 'Github: git authentication' and 'Git: Terminal Authentication'
![Settings page in VsCode](/CheatSheet/assets/static/git-auth-vscode.png)
Now clean your computer by running:
```
# First check if the following command outputs something with vscode:
git config credential.helper
# Then run this one:
git config --unset credential.helper

# First check if the following command outputs something with vscode:
git config --global credential.helper
# Then run this one:
git config --global --unset credential.helper

# First check if the following command outputs something with vscode:
git config --system credential.helper
# Then run this one:
sudo git config --system --unset credential.helper

# Then to not have to type your username and password every time:
git config credential.helper store
```
Now when you run for example ```git push``` the terminal will prompt you (in VsCode on the top of your screen) for your credentials.
For the password you must create a personal access token: <br>
[github.com/settings/personal-access-tokens](https://github.com/settings/personal-access-tokens)
![PAT screen in GitHub](/CheatSheet/assets/static/git-auth-PAT.png)
Then use that PAT as your password when prompted by git