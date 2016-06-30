# GITTE - GIT USEFUL COMMANDS / GIT CHEAT SHEET

##### Commands marked with '=>' are aliases. See .gitconfig file for details.

Display defined aliases
```
=> git alias
```

-------------------

Create a repository
```
git init                           // init empty repository
git clone remoteRepo localDir      // clone git repo to local directory
=> git makegitrepo                 // create git repo, add README.md file and make initial commit
```

-------------------

Observe your repository
```
=> git s                                       // git status
=> git st                                      // git status -sb
```
------------------

Make a change :
```
git add <filename>                              // add file with given filename
git add *                                       // add all files 	
=> git co -m "Commit message"                   // commit staged files
=> git save Commit message                      // stage and commit files with message
=> git amend Commit message                     // make stage & commit with amend 
```

-------------------

Undo local changes && differences
```
git checkout -- <filename> 						// undo specific file
git diff <branch name>							// compare changes with other branch
git diff --stat <firstBranch> <secondBranch>	// compare two branches based on statistics
git revert <commit> 		// generate a new commit that undoes all of the changes introduced in <commit>
```

-------------------

Synchronize
```
git remote 		// check defined remote repositories
git remote add origin <remote repo address> 	// add remote repository
git push -u origin <branch name>		// push given branch to origin remote repo with tracking
git push origin --delete quickFix	// delete remote branch
git fetch origin		// get the changes from remote repo (without merge)
git pull origin/master	// get the changes and merge
git pull --rebase origin/master //get the changes and do rebase
```
-------------------

Branches
```
git br                                                  // git branch
git ch                                                  // git checkout

git branch -v 		// list of local branches
git branch -r		// list of remote branches
git branch <branch name>	// create new local branch with given name
git branch -d <branch name>	// delete branch with given name
git checkout <branch name> 	// switch to specific branch
git checkout -b <branch name>	// create and swith to new branch

git merge <branch name>	// merge to actual branch from given branch name
git merge --no-ff <branch name>	// merge to actual branch without fast forward
git merge <branch name> --no-commit --no-ff // merge to actual branch without fast forward and auto commit

# for rebasing new branch instead of merging
git checkout experiment # switch to that branch
git rebase master # rebase it to selected branch, in this case move it on the top of the master
```

-------------------
Tags
```
git tag											// list of tags
git tag UMnieDziala								// create new tag
git tag -a UMnieDziala -m "Tag message" 		// create new tag with message
git tag 1.0.0 <commitID>	//use tagging to mark a significant changeset, such as a release
git push --tags origin 		//push all tags to remote repository
```
-------------------
Stash
```
git stash list 	// show stashes
git stash 		// save stash
git stash apply		// get changes from stash
git stash drop		// clear stash
```
-------------------
##### Git Rebase For Linear History
```
git commit
git pull
git rebase -i origin/master
git push origin master
```
--------------------------
#### Modify specified commit

You can use git rebase, for example, if you want to modify back to commit bbc643cd, run

	$ git rebase --interactive bbc643cd^

In the default editor, modify 'pick' to 'edit' in the line whose commit you want to modify. Make your changes and then stage them with

	$ git add <filepattern>

Now you can use

	$ git commit --amend

to modify the commit, and after that

	$ git rebase --continue

--------------------------


UPDATE FORK

1. Add the remote, call it "upstream":  
```git remote add upstream https://github.com/whoever/whatever.git```
2. Fetch all the branches of that remote into remote-tracking branches, such as upstream/master:   
```git fetch upstream```
3. Make sure that you're on your master branch:   
```git checkout master```
4. Rewrite your master branch so that any commits of yours that aren't already in upstream/master are replayed on top of that other branch:   
```git rebase upstream/master && git push -f origin master```

So everything looks like:
```
git remote add upstream https://github.com/whoever/whatever.git
git fetch upstream
git checkout master // no needed if you are on master
git rebase upstream/master 
git push -f origin master
```

#### Sources:

- https://github.com/jakubnabrdalik/gitkurwa
- http://helion.pl/ksiazki/git-rozproszony-system-kontroli-wersji-wlodzimierz-gajda,gitroz.htm?utm_campaign=videopoint&utm_medium=redirect&utm_source=
