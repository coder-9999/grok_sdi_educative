### Git Branching ###
  * git branch \<branch> : creates a new branch pointing to the same commit you’re currently on, but it only creates a new branch — it didn’t switch to that branch. HEAD will still be pointing to current branch.
  * git branch -d \<branch> : delete the local branch. Makes sure you are on diffrent branch when deleting any branch
  * git checkout \<existing-branch> : switch to an existing branch <sup>1</sup>
  * git checkout -b \<branch> : Switch to an existing branch or create new branch if one does not already exists and switch to it. <sup>1</sup>
  * git log : show commit history below the branch you are currently on.
  * git log \<branch> : show commit history below the branch specified.
  * git log --oneline --decorate --graph --all : prints commit graph of you repo
  * git checkout \<A> ; git merge \<B> : merge branch B to branch A
  
  <b>
  <sup>1</sup> --If your working directory or staging area has uncommitted changes that conflict with the branch you’re checking out, Git won’t let you switch branches. There are ways to get around this (stashing and commit amending
  </b>
