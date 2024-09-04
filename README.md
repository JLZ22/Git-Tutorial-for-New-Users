# Git-Tutorial-for-New-Users

DISCLAIMER: This tutorial only covers using git at an introductory level. It is not meant to replace documentation.<br>

This is a repository. A repository is essentially a collection of files and folders. Github stores these repositories on their servers. To get the repository on to your machine, <br> 

- click on the green button that says code and copy the link.<br>
- open the location you want the repository to be stored on you local device in the terminal<br>
- type `git clone <the link you copied>`<br>

## Branches<br>

Git is powerful because it allows you to maintain many different sandboxes of your project. Each one of these is called a branch so modifications to one branch will have no effect on others.<br>

Every repository has a *main* branch which, for most projects, will be the branch that stores the functioning version of our project. As such, we will never directly edit this branch (more on this in a later section). Instead, create a new branch with a name that most appropriately describes what you are working on (i.e. writing-readme).<br>

Branch names should be more or less a general task. After it is complete, the branch can be merged with the main branch (more on this in a later section). This ensures that if anything goes wrong, it does not affect the funcitoning code. Additionally, it prevents multiple contributors from making changes that would impact eachother's code.<br>

Below are some important commands to know for branching. 

### View all the branches of a repository<br>

`git branch -a`<br>

### Create a new branch<br>

`git branch <insert branch name>`<br>

### Switch branches<br>

`git switch <insert branch name>`<br>

## Commits<br>

Commits are snapshots of a branch's edit history, and they are created by the developer in order to record and save progress. Keep in mind that every branch has its own commit history. You typically make a commit after finishing a relatively small subtask. These commits are stored locally for now.<br>

### To make a commit, follow the steps below.<br>

- `git add -A`<br>
- `git commit -m "<insert brief description of accomplishents>"`<br>
- `git push`<br>

### To commit a specific file<br>

- `git add <insert file name 1>`<br>

If this does not work, there should be alternative instructions provided in the terminal. 

## Pushing

To move your changes from your machine to Github, run<br>

`git push`.<br>

There are certain cases where this will not work. Typically, this is because the branch that you are pushing to has changes that you did not [pull](#pulling) before working. A brief but not comprehensive solution can be found by [stashing](#stashing), [pulling](#pulling), and restoring your changes from the [stash](#stashing). Another solution you may come across is to force the push. **UNDER ALMOST NO CIRCUMSTANCES DO YOU WANT TO FORCE PUSH.** It will almost always result in merge conflicts or overwriting someone else's code.<br>

You may run into an issue where the terminal asks you to log in with an authentication token. This will be discussed in the next section.

## Github CLI

**TODO**

## Pulling <br>

When you pull, you retrieve the most recent record of your branch from github. It is strongly recommended to do this every time before you work on the code to avoid version conflicts when pushing. To pull from the branch that you are currently on simply run `git pull`. Since you will eventually want to merge the branch you are working on with the main, it is recommended to pull from main as well. This can also fail if you have changes that will be overwritten by the pull command. A simple solution is to stash your local changes before pulling. More on this in the [stashing](stash) section. 

## Stashing<br>

For the reasons stated above, sometimes we need to save our local changes before pulling. Another reason could be if you want to switch branches without committing yet. To save your work, you can use `git stash` which will push your new stash onto the stack. You can call this multiple times, so to view a list of all stashes in the branch, you can call `git stash list`. Now, you can pull and switch branches as you wish. When you want to add your most resent stash back, use `git stash apply`. If you want to restore an older stash, use `git stash apply stash@{<insert stash number>}`. Every repository has its own stash, so this is a good way to apply changes from one branch to another without needing to merge or commit anything.<br>

## Pull Requests<br>

Not to be confused with pulling, a pull request is a service offered by Github that allows developers to merge different branches. This is how we will be merging the working branches to the functional code. When you are ready to merge the branch you are working on with the main branch, you can open a pull request on Github. This allows you to compare any conflicts before making changes. More on this on Github's guide to [pull requests](https://docs.github.com/en/pull-requests).

## Git Ignore<br>

With any project, there may be certain files/directories that you do not want to be included when making commits. These can include but are not limited to virtual environments and IDE config files/folders that you need but may vary from person to person. To ignore certain files/directories, you want to create a file called `.gitignore`. In this file, you put the names of all the files and directories that you with to ignore. Here is an example of the contents of a `.gitignore`:<br>

```
example.txt
some_directory/
*.exe
```

In the example above, git will ignore the file `example.txt`, the directory `some_directory` and all of its contents, and all executables with the file type `.exe` that are found in the repository. This last line where we use `*` is an example of wildcarding which you can read more on [here](https://en.wikipedia.org/wiki/Wildcard_character). You can find more about `.gitignore` [here](https://www.atlassian.com/git/tutorials/saving-changes/gitignore).<br>


## Useful commands<br>

`git status`: shows you relevant information about your working directory<br>
`git log`: shows commit history (this is where you get commit id for git revert)<br>
`git revert <commit id>`: revert commit changes of the commit with the given id<br>

[More useful commands](https://www.loginradius.com/blog/engineering/git-commands/)

