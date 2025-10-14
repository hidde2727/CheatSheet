## Assumptions
It is assumed your terminal is inside your git project folder, or you ran
```console
cd /path/to/project/folder
```

## Initializing a repository

### From a local project:
First create a GitHub project then from a terminal inside your local project:
!!! The GitHub project must be EMPTY !!! (No ReadMe/.gitignore)
```console
git remote add origin https://github.com/<YourUsername>/<YourProjectName>.git
git push
```
You can replace origin with another remote name

### From an existing GitHub project:
First navigate to the folder where you want to place the repository, then:
```console
# Note that this will create a folder with the name YourProjectName
git clone https://github.com/<YourUsername>/<YourProjectName>.git
```

## Setting git information
```console

```