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
!!! The GitHub project must be EMPTY !!! (No ReadMe/.gitignore) <br>
Then from the terminal inside your local project:
```shell
git remote add origin https://github.com/{YourUsername}/{YourProjectName}.git
git push
```
You can replace origin with another remote name

#### From an existing GitHub project:
First navigate to the folder where you want to place the repository, then:
```shell
# Note that this will create a folder with the name YourProjectName
git clone https://github.com/{YourUsername}/{YourProjectName}.git
```

## Setting git information
Please note that setting your git username and email will expose both to the internet (If you are also using GitHub) <br>
So please use only your first name and you can use the [GitHub private email](https://docs.github.com/en/account-and-profile/how-tos/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/setting-your-commit-email-address)<br> 
The private email will look something like: 93196280+hidde2727@users.noreply.github.com
```shell
git config --global user.name "Your name"
git config --global user.email "Your email"
```

## Commiting
To commit to the **current branch** you are on use:
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
#### Change current
To change the current branch that you are on use:
```shell
git checkout {branchname}
```
**Make sure to first commit changes before using checkout**: files may else be deleted
#### Create
To create a branch that branches from the current branch you are on use:
```shell
git branch {your new branch name}
# You probably want to start using the branch as well:
git checkout {your new branch name}
```

#### Merging
After a while you probably want to merge your changes back into another branch <br>
You can either use the local GIT, or you can use GitHub
###### Local git
```shell
# Switch to the branch that will receive the merge
git checkout {your receiving branch name}
# Make sure the branch is up to date
git fetch
# Merge (make sure it creates a commit message with --no-ff)
git merge --no-ff {branch name to merge}
# Optionally delete the branch that was merged
git branch -d {branch name to merge}
```

###### Github
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
#### Push
Use the following command if your remote (for example GitHub) doesn't have changes that you have locally
```shell
git push
```