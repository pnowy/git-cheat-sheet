# GITTE - GIT CHEAT SHEET

##### Commands marked with '=>' are aliases. See .gitconfig file for details.

##### Display defined aliases
```
=> git alias
```

-------------------

##### Create a repository
```
git init                               // init empty repository
git clone [remoteRepo] [localDir]      // clone git repo to local directory
=> git makegitrepo                     // create git repo, add README.md file and make initial commit
```

-------------------

##### Observe your repository
```
=> git s                                       // git status
=> git st                                      // git status -sb
=> git stat                                    // repository statistics
git diff                                       // show changes to files not yet staged
=> git difff                                   // highlight changed words using only colors (without plus and minus)
git diff HEAD                                  // show all staged and unstaged changes
git diff commit1 commit2                       // show the changes between two commits ids
git diff <branch name>                         // show the changes regarding other branch
git diff --stat [firstBranch] <secondBranch>   // compare two branches based on statistics
git blame                                      // annotate the file
git log                                        // show full change history
git log -p [file/directory]                    // show change history for file/direcotyr including diffs
=> git llog                                    // show pretty list of lat 25 commits (id, timestamp, user, message)
=> git ltree                                   // show pretty graph from logs
=> git hist                                    // show pretty graph with history
=> git histfull                                // show pretty graph with history + changed files
=> git changelog                               // show commit messages list
=> git changelogextended                       // show commit messages list with date, author, etc.
=> git days                                    // dates of commits
```
------------------

##### Make a change :
```
git add [file]                                  // stage a file with given filename
git add .                                       // stage all changed files, ready for commit
=> git co -m "Commit message"                   // commit staged files
=> git save Commit message                      // stage and commit files with message
=> git amend Commit message                     // make stage & commit with amend
git reset [file]                                // unstages file, keeping the changes
git checkout -- [filename]                      // undo specific file if unstaged
git reset --hard                                // revert everything to the last commit
git revert [commit]                             // generate a new commit that undoes all of the changes introduced in [commit]
=> git unstage                                  // remove everything what was prepared for commit (git reset HEAD --)
```

-------------------
##### Stash
```
git stash list                                   // show stashes
git stash                                        // save stash
git stash apply                                  // get the changes from top/last stash
git stash apply [id]                             // get the changes from specified stash
git stash drop                                   // clear stash
=> git sth                                       // stash with untracked files too
```

-------------------

##### Working with branches
```
=> git br                                          // git branch
git branch                                         // list all local branches
git branch -r                                      // list of remote branches
=> git bbranch                                     // extended info about local branches
=> git branches                                    // detailed info about local and remote branches
=> git ch                                          // git checkout
git checkout [branch]                              // switch to specific branch
git checkout -b [branch]                           // create and swith to new branch
git branch [branch]                                // create new local branch with given name
git branch -d [branch]                             // delete branch with given name
git merge [branch]                                 // merge to actual branch from given branch name
git checkout [branchB] && git merge [branchA]      // merge branchA into branchB
git merge --no-ff [branch]                         // merge to actual branch without fast forward
=> git mergenoff [branch]                          // merge to actual branch without fast forward
git merge [branch] --no-commit --no-ff             // merge to actual branch without fast forward and auto commit
```

-------------------

##### Synchronize
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

##### Tags
```
git tag											// list of tags
git tag UMnieDziala								// create new tag
git tag -a UMnieDziala -m "Tag message" 		// create new tag with message
git tag 1.0.0 <commitID>	//use tagging to mark a significant changeset, such as a release
git push --tags origin 		//push all tags to remote repository
```

# TIPS & TRICKS

##### Rebasing new branch instead of merging
```
git checkout experiment                // switch to that branch
git rebase master                      // rebase it to selected branch, in this case move it on the top of the master
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
- ZeroTurnaround Git Cheat Sheet
