# Introduction

Basics:

1. git init - In new folder this will intialize a new git repository in the local machine
2. git add . - Adds all the changes to the stage
3. git commit -m "Message" - Commits the changes to the branch in local

Note:
If we are modifying an existing file we use
git commit -am "Message for the changes in the existing file"

Learning how to add the new repository from local to git

1.  Create a local folder and add your changes in it.
2.  If you want to push the changes to git, Go to ypur git account and create a new repository
3.  Copy the SSH id of that repo and use "git remote add origin <Link Copied>" - This adds the connection between your local repo and the remote repository
4.  Then open the git bash, check the remote repo links through "git remote -v"
5.  git push origin master - This command gives you the following text

    fatal: The current branch master has no upstream branch.
    To push the current branch and set the remote as upstream, use

        git push --set-upstream origin master

6.  Upstream means the actual remote repo to which your changes have to be pushed when "git push" is used. - In short you can use git push -u origin master
7.  Your changes will be pushed.

Note:
While using the above step 5 if you see permission denied then follow typing the below commands

1. "eval $(ssh-agent -s)" - This will start the ssh agent
2. ssh-add ~/keyfile - This will add the private key which will start the ssh connection between our local repo and the git
3. Then "git push -u origin master" will push the changes to the remote repo

# Branches:

Git branching is used to create a new version of the master branch and the changes we make in it are not reflected on master branch. Commands useful:

1. git checkout -b <branch-name> - to create a new branch and move to that from existing branch
2. git branch - to view all the branches that are available

To check the diff in the git bash terminal itself we can use:
git diff <branch-name>  
Here the branch-name is the branch with which we want to compare the changes.

When our changes are done, to get it reviewed we usually try to merge the changes with master but we do it through pull request.

1. Create a new branch, make your code changes on that branch.
2. After staging the changes and committing them in local machine, you need to push the branch to remote repository.
3. So the command for above function is "git push -u origin <branch-name>".
4. Once this change is there on the remote repository we usually have a merge request ready on our github website.
5. The reviewers check the code changes and then add comments if needed. If there is a requirement of the code changes based on the comments, we add new commits to the test branch and then raise another pull request.
6. After the merge requests are reviewed they get merged.

# Merge Conflicts:

1. Whenever we make a new branch of the master, we have the commits of master until that instance but meanwhile when we are making code changes to the new branch, teammates may have worked on their branch and merged them with master.
2. So when the new commit head of our branch and master are not matching we get merge conflicts when we try to merge them.
3. So we need to first of all select the needed changes. New ones or old ones or both the changes further resolving them and merge the branches.

Note:
Solving thee changes when the merge conflicts are in less number of files is easy. But when the changes are in many files this becomes tough. To solve this there is one method, which has to be followed before you stage your changes:

1. git stash push -> This will push the changes to a temporary stack and remove them from your branch.
2. git pull --rebase -> This will basically get the new head changes from the remote repository. Now all the changes from the remote head will be in your branch
3. git stash apply -> This will get the back the recent changes we pushed to the local stack
