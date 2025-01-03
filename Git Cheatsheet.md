# Git Cheatsheet
For more information please see the [Git Documentation](https://git-scm.com/doc)
## Key Terms
__Version Control System (VCS) or Source Code Manager (SCM)__
A VCS allows you to:
- Revert files back to a previous state.
- Revert the entire project back to a previous state.
- Review changes made over time.
- See who last modified something that might be causing a problem.
- Identify who introduced an issue and when.

__Commit (Snapshot)__
Git treats data as a set of snapshots of a mini file system. Every time you commit (save the state of your project in Git), it takes a "picture" of your files at that moment and stores a reference to that snapshot.

__Repository (Repo)__
A directory that:
- Contains your project work.
- Includes hidden files (used by Git).
Repositories can exist locally on your computer or as a remote copy on another computer.

__Working Directory__
The files visible in your computer's file system. When you edit your project files, you are working in the Working Directory.

> Note: This is different from:
> - Files saved in commits within the repository.
> - The command line's current working directory.



__Checkout__
The process of copying repository content to the Working Directory. You can checkout:
- Files
- Commits
- Branches

__Staging Area (Staging Index or Index)__
A file in the Git directory that stores information about what will go into your next commit. Think of it as a prep table where Git organizes the next commit. Files in the Staging Area are ready to be added to the repository.

__SHA (SHA Hash)__
An ID number for each commit. A SHA is:
- A 40-character string (composed of 0–9 and a–f).
- Calculated based on the contents of a file or directory in Git.
  
Example SHA:
`e2adf8ae3e2e4ed40add75cc44cf9d0a869afeb6`

__Branch__
A new line of development diverging from the main line. It allows:
- Independent development without altering the main line.
  
> Analogy: A branch is like a save point in a game. You can create a save point, try a risky move, and return to the save point if needed. Branches let you create save points on one branch and switch to another branch for independent work.

# First Time Git Configurations Commands
```
# Access your current git configurations
git config --list

# sets up Git with your name
git config --global user.name "<Your-Full-Name>"

# sets up Git with your email
git config --global user.email "<your-email-address>"

# makes sure that Git output is colored
git config --global color.ui auto

# displays the original state in a conflict
git config --global merge.conflictstyle diff3

```

# Setting Up Git on Various IDEs
```
# Atom
git config --global core.editor "atom --wait"

# Sublime Text
git config --global core.editor "'/Applications/Sublime Text 2.app/Contents/SharedSupport/bin/subl' -n -w"

# VS Code
git config --global core.editor "code --wait"
```

# Installing Git
## Windows
To download Git:
Go to [https://git-scm.com/downloads](https://git-scm.com/downloads) (opens in a new tab)
download the software for Windows
install Git choosing all of the default options
Once everything is installed, you should be able to run git on the command line. If it displays the usage information, then you're good to go!

## Mac
Git is actually installed on MacOS, but we'll be reinstalling it so that we'll have the newest version:

go to [https://git-scm.com/downloads](https://git-scm.com/downloads) (opens in a new tab)
download the software for Mac
install Git choosing all of the default options
Once everything is installed, you should be able to run git on the command line. If it displays the usage information, then you're good to go!

# Some Useful Terminal Commands
`ls` - used to list files and directories
`mkdir` - used to create a new directory
`cd` - used to change directories
`rm` - used to remove files and directories

# Various Git Commands
## Git Init
Before you can make commits or do anything else with a git repository, the repository needs to actually exist in your local directory. To create a new repository with Git, we'll use the `git init` command.

The `init` subcommand is short for "initialize", which is helpful because it's the command that will do all of the initial setup of a repository. We'll look at what it does in just a second.

Whenever you initialize a git repository, a hidden directory called `.git` is created.  The `.` in front of `git` makes the repository hidden on mac os.  This directory is your git repository!

> Note:
> Please do not edit any files in `.git`, as it might mess up the log of files in you are keeping track of.

Here's a brief synopsis on each of the items in the .git directory:

__config file__ - where all project specific configuration settings are stored.

Git looks for configuration values in the configuration file in the Git directory (.git/config) of whatever repository you’re currently using. These values are specific to that single repository.

For example, let's say you set that the global configuration for Git uses your personal email address. If you want your work email to be used for a specific project rather than your personal email, that change would be added to this file.

__description file__ - this file is only used by the GitWeb program, so we can ignore it

__hooks directory__ - this is where we could place client-side or server-side scripts that we can use to hook into Git's different lifecycle events

__info directory__ - contains the global excludes file

__objects directory__ - this directory will store all of the commits we make

__refs directory__ - this directory holds pointers to commits (basically the "branches" and "tags")

Remember, other than the "hooks" directory, you shouldn't mess with pretty much any of the content in here. The "hooks" directory can be used to hook into different parts or events of Git's workflow.

## Git Clone
`git clone` allows you to clone (copy) a remote repository to be loaded locally in your computer. Typically you write the URL after the command, i.e.

```
git clone < https://github.com/user/repository-name >
```

When cloning a repository, a new directory named after the repository name found in repository's url is created to store all files related to the repository.  You can change the name of the directory by the following command

```
git clone < https://github.com/user/repository-name > < new-directory-name >
```

## Git Status
The `git status` will tell you what Git is thinking and the state of our repository as Git sees it. You should be using  `git status` all of the time! You should get into the habit of running it after any other command. This will help you learn how Git works and it'll help you from making (possibly) incorrect assumptions about the state of your files/repository.

To run the command, simply run

```
git status
```