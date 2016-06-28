# GITTE - GIT USEFUL COMMANDS

##### Commands marked with '=>' are aliases. See .gitconfig file for details.


Create a new local repository
```
git init                           // init empty repository
git clone remoteRepo localDir      // clone git repo to local directory
=> git makegitrepo                 // create git repo, add README.md file and make initial commit
```

------------------

Staging & commit :
```
git add <filename>		// add file with given filename
git add *				// add all files 	
git commit -m "Commit message"		// commit staged files
git commit -a -m "Commit message"	// stage and commit files with message
=> git save "Commit message"		// stage and commit files with message
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

Repo status

	git status

-------------------
Remote repositories

	git remote 		// check defined remote repositories
	git remote add origin <remote repo address> 	// add remote repository

-------------------
Branches

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

-------------------
Push && Pull

	git push -u origin <branch name>		// push given branch to origin remote repo with tracking
	git push origin --delete quickFix	// delete remote branch
	git fetch origin		// get the changes from remote repo (without merge)
	git pull origin/master	// get the changes and merge
	git pull --rebase origin/master //get the changes and do rebase

-------------------
Tags

	git tag											// list of tags
	git tag UMnieDziala								// create new tag
	git tag -a UMnieDziala -m "Tag message" 		// create new tag with message
	git tag 1.0.0 <commitID>	//use tagging to mark a significant changeset, such as a release
	git push --tags origin 		//push all tags to remote repository

-------------------
Stash

	git stash list 	// show stashes
	git stash 		// save stash
	git stash apply		// get changes from stash
	git stash drop		// clear stash

-------------------
##### Git Rebase For Linear History

	$ git commit
	$ git pull
	$ git rebase -i origin/master
	$ git push origin master

--------------------------
#### Modidy specified commit

You can use git rebase, for example, if you want to modify back to commit bbc643cd, run

	$ git rebase --interactive bbc643cd^

In the default editor, modify 'pick' to 'edit' in the line whose commit you want to modify. Make your changes and then stage them with

	$ git add <filepattern>

Now you can use

	$ git commit --amend

to modify the commit, and after that

	$ git rebase --continue

--------------------------

# Przydatne obecnie aliasy:

Pokazuje ładnie commity z drzewkiem i bajerami

    git hist

To co wyżej + które pliki się zmieniły i jak

    git histfull

Pokazuje commity z czasem, autorem i tagami

    git llog

Mówi jakie commity poszły do brancha od czasu gdy pullowaliśmy tego używamy żeby sprawdzić czy coś się zmieniło

    git anychanges <NAZWABRANCHA>

Jeśli branch który nas interesuje nazywa się 'master', pokazuje co się na nim zmieniło od czasu gdy pullowaliśmy. Tego używamy żeby sprawdzić czy coś się zmieniło w 90% projektów SVNo-podobnych.

    git anychangesonmaster

Mówi kto ostatnio coś zmieniał (tzn. od czasu gdy pullowaliśmy)

    git whoischanging <NAZWABRANCHA>

Jeśli branch który nas interesuje nazywa się 'master', mówi kto ostatnio coś zmieniał (tzn. od czasu gdy pullowaliśmy)

    git whoischangingmaster

Wyświetla tagi z hashami

    git showtags

Tworzy taga z datą/godziną i przedrostkiem, np: PRZEDROSTEK_12-01-12_15-25-25

    git tagwithdate <PRZEDROSTEK>

Domyślnie tagi nie wędrują na serwer zdalny przy pushu. Trzeba je popchnąć 'specjalnie'. Np. tą komendą (nie żeby oryginał był dłuższy).

    git pushtags

Mówi nam trochę więcej o osobie. Pomocne zwłaszcza gdy ktoś nie skonfigurował sobie gita

    git whois <email lub nazwa>

Mówi nam jaki był ostatni commit w tym czymś co podaliśmy

    git whatis <BRANCH/TAG/WHATEVER>

Mówi jakie branche mamy w origin, kto je modyfikował i kiedy. Bardzo przydatne przy używaniu gitflow i feature branchach, żeby się zorientować, co się dzieje w projekcie (i kto/kiedy robił). Wymaga aktualnej wizji repo lokalnie (czyli git fetch origin wcześniej)   

    git showorigin

Inny sposób prezentacji wszystkich branchy - jeszcze bardziej szczegółowy

    git branches

UPDATE FORK

1. Add the remote, call it "upstream":  
```git remote add upstream https://github.com/whoever/whatever.git```
2. Fetch all the branches of that remote into remote-tracking branches, such as upstream/master:   
```git fetch upstream```
3. Make sure that you're on your master branch:   
```git checkout master```
4. Rewrite your master branch so that any commits of yours that aren't already in upstream/master are replayed on top of that other branch:   
```
   git rebase upstream/master 
   git push -f origin master
```
