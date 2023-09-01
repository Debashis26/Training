# Git

[**What is git ?**](https://git-scm.com/)  
Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

[ **Version control** ](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)  
Version control is a system that records changes to a file or set of files over time so that we can recall specific versions latter.

_Local Version Control system_  
 Copy files to an another directory is the easyest way to do version controlling, but it can also error prone.  
 To deal with thiss issue, programmersmlong ago developed local VCSs that had a simpple database that kept all the changes happens with the file under version control system.

_Centralized Version Control System_

The next major issue that people encounter is that, they need to collaborate with developers on other syatem. To deal with this problem _Centralized Verson control (CVCSs)_ is interduced.

The system have a single server that contains
all the versioned files, and a number of clients that check out files from that central place. For many
years, this has been the standard for version control.  
This setup also has some serious downsides. The most obvious is the single point of failure. If that server goes down, then during this time nobody can collaborate at all or save versioned changes to anything they’re working on.

_Distributed Version Control Systems_

This is where Distributed Version Control Systems (DVCSs) step in.In a DVCS (such as Git, Mercurial,
Bazaar or Darcs), clients don’t just check out the latest snapshot of the files; rather, they fully
mirror the repository, including its full history.  
Thus, if any server dies, and these systems were
collaborating via that server, any of the client repositories can be copied back up to the server to
restore it. Every clone is really a full backup of all the data.

## Git Operationstouch

[**Basic Operation**](https://www.atlassian.com/git/glossary)

**Git Config :**
The [`git config`](https://www.atlassian.com/git/tutorials/setting-up-a-repository/git-config#:~:text=The%20git%20config%20command%20is,modify%20a%20configuration%20text%20file.) command is a convenience function that is used to set Git configuration values on a global or local project level.  
 _command_  
 user.name- `$ git config --global user.name "Your Name Comes Here"`

user.email- `$ git config --global user.email "you@yourdomain.example.com"`

**👉 Working with new project**

**1.Git init :**  
Initializes a new Git repository. If you want to place a project under revision control.  
_command:_ `$ git init`

**Git status :**  
Displays the state of the working directory and the staged snapshot. You’ll want to run this in conjunction with git add and git commit to see exactly what’s being included in the next snapshot.  
_command :_ `$ git status`

**Git add**  
Moves changes from the working directory to the staging area. This gives you the opportunity to prepare a snapshot before committing it to the official history.

add selected untracked file-  
 `$ git add file1`  
or  
 `$ git add file1 file2 file3`

add all untracked file at once-  
`$ git add .`

[Q. what is the role of . in git add . ?](https://www.designcise.com/web/tutorial/what-does-git-add-dot-do#:~:text=The%20dot%20in%20the%20git,in%20directories%20above%20and%20below)  
The dot in the git add . command is simply a pathspec (which may also be a filepath), that tells git to only look for changed files in the current directory (i.e. it omits paths found in directories above and below).

**Git commit**  
Takes the staged snapshot and commits it to the project history. Combined with git add, this defines the basic workflow for all Git users.  
_command :_ `$ git commit -m  "commit message"`

**Git branch**  
This command is your general-purpose branch administration tool. It lets you create isolated development environments within a single repository.

_Common Options:_  
`$ git branch `: List all of the branches in your repository. This is synonymous with `$ git branch --list`.

`$ git branch <branch-name> `: Create a new branch called < branch-name >. This does not check out the new branch.

`$ git branch -d <existing-branch-name> `: Delete the specified branch. This is a “safe” operation in that Git prevents you from deleting the branch if it has unmerged changes.

`$ git branch -D <existing-branch-name>` : Force delete the specified branch, even if it has unmerged changes. This is the command to use if you want to permanently throw away all of the commits associated with a particular line of development.

`$ git branch -m <renamed-branch-name>` : Rename the current branch to < renamed-branch-name>.

`$ git branch -a`: List all remote branches.

_Creating remote branches_  
`$ git remote add <ref-name > <url> ` :Add remote repo to local repo config.  
`$  git push <ref-name> <branch-name >` :
push the < branch-name> to < ref-name >

---

**👉 Working with existing project**

**Clone repo :**  
Creates a copy of an existing Git repository. Cloning is the most common way for developers to obtain a working copy of a central repository.  
_command :_ `$ git clone <repo-url >`

**Pull from repo :**  
Pulling is the automated version of git fetch. It downloads a branch from a remote repository, then immediately merges it into the current branch.

_command :_ `$ git pull < remote-name > < branch-name >`

**Fetch from repo :**  
Fetching downloads a branch from another repository, along with all of its associated commits and files. But, it doesn't try to integrate anything into your local repository. This gives you a chance to inspect changes before merging them with your project.

_command :_ `$ git fetch `

**Git merge**
A powerful way to integrate changes from divergent branches. After forking the project history with git branch, git merge lets you put it back together again.  
_command :_ `$ git merge `

**👉 Push the files to remote repo**

**Git push :**  
The git push command is used to upload local repository content to a remote repository. Pushing is how you transfer commits from your local repository to a remote repo.  
_Command :_ `$ git push < remote-name > < branch-name>`

[**Git strategy**](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)

Git Flow and Trunk Based Development are two different approaches to managing version control and the development workflow in software projects. They have different philosophies and implications for how code is managed, integrated, and released within a development team.

**Git Flow:**  
Git Flow is a branching model for Git that defines a specific branching strategy and workflow for managing code changes. It was popularized by Vincent Driessen in a blog post. The main idea behind Git Flow is to provide a structured approach to managing different stages of development and releases. It involves several long-lived branches:

_Master/Branch:_  
The master branch represents the stable codebase. It's intended to always contain production-ready code.

_Develop/Branch:_  
The develop branch is where ongoing development takes place. Feature branches are typically merged into this branch.

_Feature/Branch:_  
Feature branches are created for specific features or tasks. They branch off from develop and are merged back into it once the feature is complete.

_Release/Branch:_  
When preparing for a release, a release branch is created from develop. It's used for finalizing and testing the code before deploying it to production.

_Hotfix/Branch:_  
If critical bugs are discovered in the production code, a hotfix branch is created from master, the bug is fixed, and the change is merged back into both master and develop.

While Git Flow provides a clear structure for managing development stages, it can lead to longer release cycles and more complex merge processes, especially when dealing with feature branches that diverge significantly over time.

**Trunk Based Development:**  
Trunk Based Development is an approach that promotes simpler and more frequent integration of code changes. The main principle is to keep the master branch (or a similar mainline branch) in a releasable state at all times. Developers work directly on short-lived feature branches and integrate their changes into the mainline branch multiple times a day. This approach encourages smaller, more incremental changes and aims to reduce merge conflicts.

In Trunk Based Development:

_Feature/Branch_:  
Developers create short-lived feature branches for specific tasks or features. These branches are integrated into the mainline branch as soon as they're ready.

_Mainline/Branch:_  
The mainline branch, often referred to as master, is always in a state that could potentially be released. Integration happens frequently and is usually automated through continuous integration tools.

Trunk Based Development aims to minimize the overhead of managing multiple long-lived branches and encourages a fast-paced development cycle. However, it requires a strong focus on automated testing and continuous integration to ensure that the mainline remains stable.

In summary, Git Flow provides a structured approach with distinct branches for different development stages, while Trunk Based Development promotes frequent integration into a stable mainline branch. The choice between these approaches depends on the team's development philosophy, the nature of the project, and the development practices they wish to adopt.

[By ChatGPT](https://chat.openai.com/share/f0a48459-e26d-4eb0-97b2-af9c53412dac)

<img src="https://lanziani.com/slides/gitflow/images/gitflow_1.png" alt="Description of the image" style="width:450px; height:300px;"><br/>_git flow_

<img src="https://convincedcoder.com/images/2019-02-16-Trunk-based-development/feature-branch.png" alt="Description of the image" style="width:550px; height:300px;"><br/>_Trunk based Development_

## Bash

Bash is a shell program, which is basically a command line interpreter that typically runs in a text window where user can intract with the system by writing the command or script. It is a type of Unix like shell.

**Shell :**  
it is the Command Line Interface (CLI) used to intract with the system resources directely.

[**Basic Bash Command**](https://www.educative.io/blog/bash-shell-command-cheat-sheet)

1. `ls` : list the files and directories in the current directory.

   ```Bash
   $ ls
   ```

2. `mkdir` - create a new directory.
   ```Bash
   $ mkdir <dir-name>
   ```
3. `cd` - change the current directory.
   ```Bash
   $ cd <dir-name>
   ```
4. `rmdir` - remove a directory
   ```Bash
   $ rmdir <dir-name>
   ```
5. `pwd` - print the current working directory
   ```Bash
   $ pwd
   ```
6. `cp` - copy files or directories

   ```Bash
   #We will copy a file called #example.txt from the current directory to a directory called backup

   $ cp example.txt backup/
   ```

7. `mv` - move or rename files or directories
   ```Bash
   $ mv < file-path/name> <destination-path >
   ```
8. `rm` - remove files or directories
   ```Bash
   $ rm <file-name>
   ```
9. `touch` - create a new empty file or update the timestamp of an existing file
   ```Bash
   $ touch <file-name>
   ```
10. `cat` - concatenate and display files

    ```Bash
    $ cat <file-name>
    ```

11. `htop` - an interactive process viewer and system monitor
    ```Bash
    $ htop
    ```
12. `ping` - test network connectivity
    ```Bash
    $ ping www.googlee.com
    ```
13. `ifconfig` - display or configure network interfaces
    ```Bash
    $ ifconfig
    ```
14. `netstat` - display network connection information
    ```Bash
    $ netstat
    ```
15. `top` - display system resource usage and processes
    ```Bash
    $ top
    ```
16. `su` - switch user to become another user
    ```Bash
    $ su <user-name>
    ```
17. `sudo` - execute a command as another user or with elevated privileges
    ```Bash
    $ sudo
    ```
18. `df` - display disk space usage
    ```Bash
    $ df
    ```
19. `du` - display disk usage by file or directory
    ```Bash
    $ du
    ```
20. date - display or set the system date and time

```Bash
$ date
```

21. `finger` - displays all the information about user
    ```Bash
    $ finger <user-name>
    ```
22. `history` - display a list of previously executed commands
    ```Bash
    $ history
    ```
23. `echo` - display text or variables to the console
    ```Bash
    $ echo <text>
    ```
24. `locate` - locate any file on the system
    ```Bash
    $ locate <file-name>
    ```
25. `cat` - display the content of the file.
    ```Bash
    $ cat <path/file-name>
    ```
26. `Vim` is a text editor used to create, edit the text file.

    ```Bash
    # create new file
    $ vim <file-name.txt>
    ```

    ```Bash
    # view the content
    $ vim <file-name>
    ```

    _note:_  
    i. If you want to edit the the text file, Go to Insert Mode: Press’ I’ from the keyboard to switch from command mode to insert mode. At the bottom of the editor, you can see INSERT.

ii. Save the file and exit from the editor: To save and exit from it, you can press the [Esc] key and the ‘:wq.’.

iii. `Esc +:w` – Save the file but do not exit.  
 `Esc +:q!` – To quit the file without first saving what you were working on.  
 `Esc +:wq` – To save the file and exit from Vim.

27. `ls -l` - View the details of a file.


    ```Bash
    $ ls -l <file name>
    # "l" option is for long
    ```
28. Remove a directory (force) :
      
    ```Bash
    $ rm -r <directory name>
    ```
    ```Bash
    $ rm -rf <directory name>
    ```
    ```Bash
     # The '-r' flag tells the command to remove directories and their contents recursively, and the '-f' flag forces the removal without asking for confirmation.
    ```
