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
