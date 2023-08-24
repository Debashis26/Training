### Git

[**What is git ?**](https://git-scm.com/)  
Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.  

[ **Version control** ](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)   
Version control is a system that records changes to a file or set of files over time so that we can recall specific versions latter.  

 *Local Version Control system*   
 Copy files to an another directory is the easyest way to do version controlling, but it can also error prone.  
 To deal with thiss issue, programmersmlong ago developed local VCSs that had a simpple database that kept all the changes happens with the file under version control system.  

 *Centralized Version Control System*  

 The next major issue that people encounter is that, they need to collaborate with developers on other syatem. To deal with this problem *Centralized Verson control (CVCSs)* is interduced.  

The system have a single server that contains
all the versioned files, and a number of clients that check out files from that central place. For many
years, this has been the standard for version control.  
This setup also has some serious downsides. The most obvious is the single point of failure. If that server goes down, then during this time nobody can collaborate at all or save versioned changes to anything they’re working on.  

*Distributed Version Control Systems*  
  
This is where Distributed Version Control Systems (DVCSs) step in.In a DVCS (such as Git, Mercurial,
Bazaar or Darcs), clients don’t just check out the latest snapshot of the files; rather, they fully
mirror the repository, including its full history.  
Thus, if any server dies, and these systems were
collaborating via that server, any of the client repositories can be copied back up to the server to
restore it. Every clone is really a full backup of all the data.  

[**Basic Operation**](https://www.atlassian.com/git/glossary)  

**Git Config :** 
   The [```git config```](https://www.atlassian.com/git/tutorials/setting-up-a-repository/git-config#:~:text=The%20git%20config%20command%20is,modify%20a%20configuration%20text%20file.) command is a convenience function that is used to set Git configuration values on a global or local project level.   
   *command*  
   user.name- ```$ git config --global user.name "Your Name Comes Here"```

   user.email- ```$ git config --global user.email "you@yourdomain.example.com"```  

**👉 Working with new project**

**1.Git init :**  
Initializes a new Git repository. If you want to place a project under revision control.  
*command:* ```$ git init```  

**Git status :**  
Displays the state of the working directory and the staged snapshot. You’ll want to run this in conjunction with git add and git commit to see exactly what’s being included in the next snapshot.  
*command :* ```$ git status```  

**Git add**  
Moves changes from the working directory to the staging area. This gives you the opportunity to prepare a snapshot before committing it to the official history.

add selected untracked file-  
 ```$ git add file1.txt```  
or  
 ```$ git add file1 file2 file 3``` 

add all untracked file at once-  
```$ git add .```    

[Q. what is the role of . in git add . ?](https://www.designcise.com/web/tutorial/what-does-git-add-dot-do#:~:text=The%20dot%20in%20the%20git,in%20directories%20above%20and%20below)  
The dot in the git add . command is simply a pathspec (which may also be a filepath), that tells git to only look for changed files in the current directory (i.e. it omits paths found in directories above and below).    

**Git commit**
