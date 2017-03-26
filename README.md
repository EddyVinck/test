# GithubTest

pull alles van deze repository naar je locale folder en zet je naam in een van de list items. Push de versie met je naam erin naar deze repository.

### tutorial

deze tutorial heb ik gevolgd: https://www.youtube.com/watch?v=SWYqp7iY_Tc

en nog een paar andere tutorials
- https://www.youtube.com/watch?v=HVsySz-h9r4


### download

https://git-scm.com/downloads

### cheat sheet

https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf

veelgebruikte commands:
- $ git clone myUrl To-this-folder // clone/download repository to a specified location on your PC
- $ git init // initialize local git repository
- $ git add file.txt // add file(s) to Index
- $ git status // check status of working tree
- $ git commit -m 'Je bericht' // commit changes to Index with comment
- $ git push // push to remote repository
- $ git pull // Pull latest from remote repository


### toevoegen repository

- je voegt deze repository toe met: git remote add origin https://github.com/EddyVinck/test.git

### branches

- $ git branch [name_of_new_branch] // create  new branch
- $ git checkout [name_of_new_branch] // switch to that branch
- $ git branch // see all current branches and in which branch you currently are
- $ git push origin [name_of_your_new_branch] // Push the branch on github
- $ git push -u origin [name_of_your_branch] /* push branch to remote repository and the -u tells git that you want to associate your local branch with the remote branch. This allows you to just use '$ git pull' and '$ git push' in the future without specifying to/from where you want to push or pull. */
- $ git merge [name_of_your_branch] // merge [name_of_your_branch] to local master(assuming you are in the master branch)
- $ git push origin master // push merged branch to remote repository
- $ git branch --merged // shows which branches have been merged to the current branch
- $ git branch -d [name_of_your_new_branch] // Delete a branch on your local filesystem
- $ git push origin --delete [name_of_your_new_branch] // Delete branch on Github

#### branch: common workflow

stel dat je aan een rekenmachine werkt. Je zit in je master branch en je wilt een deelfunctie toevoegen.
- $ git branch subtract
- $ git checkout subtract
- // voeg functie toe
- $ git status
- $ git add .
- $ git commit -m 'subtract function'
- $ git push -u origin subtract
- $ git checkout master
- $ git pull origin master // omdat je in een andere branch hebt gewerkt, wil je zeker weten dat je wel alle andere veranderingen die door anderen in de tussentijd zijn gemaakt ook in je locale folder krijgt.
- $ git merge subtract // merge subtract with master
- $ git push origin master // push those changes

### Extra

Stel dat je iets upload wat je lokaal wel wilt houden maar van github af wil gooien dan:
- $ git rm --cached document.docx // remove a file from git/remote repository
- $ git commit -m "removed unwanted file.docx"
- $ git push


folder/map verwijderen van gitgub:
- $ git rm -r --cached myFolder // remove folder in git/remote repository

folder lokaal verwijderen:
- $ git rm -r myFolder // remove local folder

clone naar huidige folder:
- $ git clone myUrl . // clone to current folder

bekijk bestanden in huidige folder
- $ ls
- $ ls -la // more details

naar een andere map/locatie gaan:
- $ cd /nestedFolder
- $ cd .. // go to parent folder

informatie over remote repository bekijken
- $ git remote -v // view local folder(fetch) and remote repository(push)

### damage control

De meeste informatie uit dit stuk heb ik van deze tutorial: https://www.youtube.com/watch?v=FdZecVxzJbk

veranderingen aan een bestand terugzetten als ze nog niet gecommit zijn:
- $ git checkout index.html // bestand wordt gereset

foutieve commit message goedzetten(alleen doen als je dit nog niet gepushed hebt):
- $ git commit --amend -m 'new message'

achteraf een bestand nog aan een commit toevoegen(alleen doen als je nog niet gepushed hebt)
- $ git add file.txt
- $ git commit --amend // open interactive editor
- enter :wq to save and close out the editor
- $ git log // shows commits. This will show that no extra commit was created.
- $ git log --stat // this will show the files that were changed within the commit

stel dat je per ongeluk in de verkeerde branch hebt gecommit
- step 1: Move the commit to right branch
- step 2: Return master branch back to the state of only having the original commits
- // step 1
- $ git log // you need the hash
- $ git checkout subtract-feature
- $ git cherry-pick [first 10 characters of hash] // cherry-pick creates a new commit based off of the original. the commit that was incorrectly committed to master has now also been committed to subtact-feature. Now we need to delete it from the master branch:
- // step 2
- $ git checkout master
- $ git log // grab hash from the commit before the incorrect commit
- // pick the right reset: soft, mixed or hard
- $ git reset --soft [hash] // not what you want because it will keep the changes in the staging directory
- $ git reset [hash] // mixed is default, keeps the changes but only in the working directory so this isn't what you want either
- $ git reset --hard [hash] // make all the *tracked* files match the state they were in at the hash that you specify. It will get rid of your changes from the hash.
- $ git status // see if there are any untracked files that were changed
- $ git clean -df // get rid of any untracked directories and files
- $ git log //

stel dat je per ongeluk iets hardreset dan kun je binnen een bepaalde tijd die veranderingen toch terug halen
- $ git reflog // gives all the latest changes with the associated hash
- $ git checkout [hash] // you now have your changes back
- // as you can see you are now in the [hash] branch(a detached HEAD)which will be deleted over time.
- $ git branch backup
- $ git branch
- $ git checkout master
- $ git branch // the detached HEAD branch no longer shows up once you checkout a different branch, however if it has not been over 30 days it probably still exists if you access it with the hash
- $ git checkout backup // you still have the changes that you thought you had lost

if you have already pushed changes, you want to use '$ git revert' which creates new commits to reverse the effect of some earlier commits(so you don't modify earlier commits/change history which could lead to problems in the future)
- $ git log
- // copy first 10 characters of hash
- git revert [hash]
- // enter :wq [enter] // save and exit
- $ git log // see that the hash was reverted(the revert itself also has a hash)
- $ git diff [hash] [reverted-hash] // show the difference between the two hashes
- // again, this is necessary because when somebody pulls this down their history will not be corrupted