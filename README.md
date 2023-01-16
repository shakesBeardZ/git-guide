# Git Guide for IOP team 

## 1. Introduction 

Git is a distributed version control software that basically allows multiple people to work in parallel and it saves a history of all changes made. This will help ensure that there are no code conflicts as well as allow developers the ability to revert files or entire projects back to a previous version of their code.

Git can track what changes were made, who made the change, when they made the change, and why they made the change. How cool is that? Better yet, it’s all free!


## 2. Git Vs GitHub 

a lot of people mix the two tools although they are totally different, git is the tool that manages the source code it can be installed on any platform (Linux, MacOs...).
in the other hand Github is a cloud platform used to host the code and it is git compatible much like Gitlab or Bitbucket they are all cloud platforms 


## 3. git commands and concepts 


1.  Create a local git repository 
    ```
    mkdir your-project-dir
    cd [your-project-dir]
    git init
    ```

2. checking out a repository 
    sometimes we need to pull a project and start working on it we call this in Git world cloning a repo.
    ```
    git clone /path/to/repository
    ``` 
3. workflow 

    your local repository consists of three "trees" maintained by git. the first one is your Working Directory which holds the actual files. the second one is the Index which acts as a staging area and finally the HEAD which points to the last commit you've made.

    ![trees](https://user-images.githubusercontent.com/15571628/212670263-84dfc6ca-8cfe-40d4-b1d8-14d427f222e5.png)

4. add & commit 
    You can propose changes (add it to the Index) using 
    ```
    git add <filename>
    or
    git add .
    ```
    This is the first step in the basic git workflow. To actually commit these changes use
    ```
    git commit -m "Commit message"
    ```

    Now the file is committed to the HEAD, but not in your remote repository yet.

5. Ignoring Files in Commit 
    we can tell git to ignore some files and to not track them by creating a ```.gitignore``` file in the working directory.

    example of ```.gitignore``` file.

    ```
    /node_modules
    /.pnp
    .pnp.js
    ```

6. pushing changes
    Your changes are now in the HEAD of your local working copy. To send those changes to your remote repository, execute
    ```
    git push origin master
    ```
    Change master to whatever branch you want to push your changes to.

    If you have not cloned an existing repository and want to connect your repository to a remote server, you need to add it with
    ```
    git remote add origin <server>
    ```

    Now you are able to push your changes to the selected remote server

7. branching 

    Branches are used to develop features isolated from each other. The master branch is the "default" branch when you create a repository. Use other branches for development and merge them back to the master branch upon completion.  
    
    ![branches](https://user-images.githubusercontent.com/15571628/212670636-ab427c3c-8d3d-4096-bf79-093b44e540c1.png)


    create a new branch named "feature_x" and switch to it using
    ```
    git checkout -b feature_x
    ```

    switch back to master
    ```
    git checkout master
    ```
    and delete the branch again

    ```
    git branch -d feature_x
    ```

    a branch is not available to others unless you push the branch to your remote repository
    ```
    git push origin <branch>
    ```

6. update & merge
    to update your local repository to the newest commit, execute
    ```
    git pull
    ```
    in your working directory to fetch and merge remote changes.

    to merge another branch into your active branch (e.g. master), use
    ```
    git merge <branch>
    ```
    in both cases git tries to auto-merge changes. Unfortunately, this is not always possible and results in conflicts. You are responsible to merge those conflicts manually by editing the files shown by git. After changing, you need to mark them as merged with
    ```
    git add <filename>
    ```

    before merging changes, you can also preview them by using
    ```
    git diff <source_branch> <target_branch>
    ```

8. log 

    in its simplest form, you can study repository history using.. ``git log`` 
    You can add a lot of parameters to make the log look like what you want. To see only the commits of a certain author:
    ```
    git log --author=bob
    ```
    To see a very compressed log where each commit is one line:
    ```
    git log --pretty=oneline
    ```
    Or maybe you want to see an ASCII art tree of all the branches, decorated with the names of tags and branches:
   ```
    git log --graph --oneline --decorate --all
    ```
    See only which files have changed:
    ```
    git log --name-status
    ```
    These are just a few of the possible parameters you can use. For more, see git log --help

