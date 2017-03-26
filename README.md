# GithubTest

pull alles van deze repository naar je locale folder en zet je naam in een van de list items. Push de versie met je naam erin naar deze repository.

### tutorial

deze tutorial heb ik gevolgd: https://www.youtube.com/watch?v=SWYqp7iY_Tc

### download

https://git-scm.com/downloads

### cheat sheet

https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf

veelgebruikte commands:
- $ git clone <url> <To this folder> // clone/download repository to a specified location on your PC
- $ git init // initialize local git repository
- $ git add <file> // add file(s) to Index
- $ git status // check status of working tree
- $ git commit -m 'Je bericht' // commit changes to Index with comment
- $ git push // push to remote repository
- $ git pull // Pull latest from remote repository


### toevoegen repository

- je voegt deze repository toe met: git remote add origin https://github.com/EddyVinck/test.git

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
- $ git clone <url> . // clone to current folder
