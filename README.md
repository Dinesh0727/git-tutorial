# Demo

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

1. eval "$(ssh-agent -s)" - This will start the ssh agent
2. ssh-add ~/keyfile - This will add the private key which will start the ssh connection between our local repo and the git
3. Then "git push -u origin master" will push the changes to the remote repo

Branches:
Git branching is used to create a new version of the master branch and the changes we make in it are not reflected on master branch. Commands useful:

1. git checkout -b <branch-name> - to create a new branch and move to that from existing branch
2. git branch - to view all the branches that are available
