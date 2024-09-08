# Git-Tutorial-for-New-Users

DISCLAIMER: This tutorial only covers using git at an introductory level. It is not meant to replace documentation.

<ins>If you find this tutorial helpful, please consider giving it a star! 😊</ins>

## What is a repository?

You're looking at one. A repository is a folder that stores other files and folders. Github stores repositories on their servers. To get the repository onto your machine,  

- click on the green button that says code and copy the link.
- open the location you want the repository to be stored on your local device in the terminal
- type  `git clone <the link you copied>`

For example, if you want to clone this repository, in your current working directory, 

```git clone https://github.com/JLZ22/Git-Tutorial-for-New-Users.git``` 

will create a directory called `Git-Tutorial-for-New-Users` in your working directory. If you navigate into `Git-Tutorial-for-New-Users`, you will find a README.md file that contains the Markdown code for what you're reading right now.

## Branches

Git is powerful because it allows you to maintain many different sandboxes of your project. Each one of these is called a branch so modifications to one branch will have no effect on others.

Every repository has a *main* branch which, for most projects, will be the branch that stores the functioning version of our project. As such, we will almost never directly edit this branch (more on this in a later section). Instead, create a new branch with a name that most appropriately describes what you are working on (i.e. writing-readme).

Branch names should be more or less a general task. After it is complete, the branch can be merged with the main branch (more on this in a later section). This ensures that if anything goes wrong, it does not affect the funcitoning code. Additionally, it prevents multiple contributors from making changes that would impact eachother's code.

Below are some important commands to know for branching. 

### View all the branches of a repository

`git branch -a`

### Create a new branch

`git branch <insert branch name>`

### Switch branches

`git switch <insert branch name>`

## Commits

Commits are snapshots of a branch's edit history, and they are created by the developer in order to record and save progress. Keep in mind that every branch has its own commit history. You typically make a commit after finishing a relatively small subtask. These commits are stored locally for now.

### To make a commit, follow the steps below.

- `git add -A`
- `git commit -m "<insert brief description of accomplishents>"`
- `git push`

### To commit a specific file(s)

- `git add FILE1 FILE2 ...`

If this does not work, there should be alternative instructions provided in the terminal. 

## Pushing

To move your changes from your machine to Github, run

`git push`.

There are certain cases where this will not work. Typically, this is because the branch that you are pushing to has changes that you did not [pull](#pulling) before working. A brief but not comprehensive solution can be found by [stashing](#stashing), [pulling](#pulling), and restoring your changes from the [stash](#stashing). Another solution you may come across is to force the push. **UNDER ALMOST NO CIRCUMSTANCES DO YOU WANT TO FORCE PUSH.** It will almost always result in merge conflicts or overwriting someone else's code.

You may run into an issue where the terminal asks you to log in with an authentication token. This will be discussed in the next section.

## Github CLI

As of August 13th, 2021, GitHub no longer accepts username + password to perform git operations ([source](https://github.com/orgs/community/discussions/29193)). Some alternatives are using an authentication token, SSH key, or Github CLI. For this tutorial, I will only be going over how to set up Github CLI. 

1. Visit this [website](https://cli.github.com/) to install Github CLI
2. Restart your terminal 
3. run `gh auth login`. This command will give you a sequence of prompts. 
    - For personal use, select `GitHub.com` 
    - Then, select `HTTPS`
    - Then, it will ask to authenticate with your Github credentials. Answer "Y" and log in with web browser by following the instructions. Alternatively, you can use an authentication token here, but that is out of the scope of this tutorial. 
4. And you're done! Now, you can run all git commands without needing to authorize them every time. Note: this is **not recommended** if you are working on a shared/temporary machine because it grants **unlimited access** indefinetly

## Pulling 

When you pull, you retrieve the most recent record of your branch from github. It is strongly recommended to do this every time before you work on the code to avoid version conflicts when pushing. To pull from the branch that you are currently on simply run `git pull`. Since you will eventually want to merge the branch you are working on with the main, it is recommended to pull from main as well. This can also fail if you have changes that will be overwritten by the pull command. A simple solution is to stash your local changes before pulling. More on this in the [stashing](stash) section. 

## Stashing

For the reasons stated above, sometimes we need to save our local changes before pulling. Another reason could be if you want to switch branches without committing yet. To save your work, you can use `git stash` which will push your new stash onto the stack. You can call this multiple times, so to view a list of all stashes in the branch, you can call `git stash list`. Now, you can pull and switch branches as you wish. When you want to add your most resent stash back, use `git stash apply`. If you want to restore an older stash, use `git stash apply stash@{<insert stash number>}`. Every repository has its own stash, so this is a good way to apply changes from one branch to another without needing to merge or commit anything.

## Pull Requests

Not to be confused with pulling, a pull request is a service offered by Github that allows developers to merge different branches. This is how we will be merging the working branches to the functional code. When you are ready to merge the branch you are working on with the main branch, you can open a pull request on Github. This allows you to compare any conflicts before making changes. More on this on Github's guide to [pull requests](https://docs.github.com/en/pull-requests).

## Git Ignore

With any project, there may be certain files/directories that you do not want to be included when making commits. These can include but are not limited to virtual environments and IDE config files/folders that you need but may vary from person to person. To ignore certain files/directories, you want to create a file called `.gitignore`. In this file, you put the names of all the files and directories that you with to ignore. Here is an example of the contents of a `.gitignore`:

```
example.txt
some_directory/
*.exe
```

In the example above, git will ignore the file `example.txt`, the directory `some_directory` and all of its contents, and all executables with the file type `.exe` that are found in the repository. This last line where we use `*` is an example of wildcarding which you can read more on [here](https://en.wikipedia.org/wiki/Wildcard_character). You can find more about `.gitignore` [here](https://www.atlassian.com/git/tutorials/saving-changes/gitignore).


## Useful commands

`git status`: shows you relevant information about your working directory

`git log`: shows commit history (this is where you get commit id for git revert)

`git revert <commit id>`: revert commit changes of the commit with the given id

[More useful commands](https://www.loginradius.com/blog/engineering/git-commands/)

