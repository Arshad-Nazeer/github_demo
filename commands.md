Configuring Git:-
git config --global user.name "My name"
git config --global user.email "someone@gmail.com"
git config --list

Clone & Status:-

Clone -> Cloning a repository on our local machine -> git clone <link>

Status -> displays the status of the code -> git status
{
    untracked: new files that git doesn't track yet,
    modified: changed,
    staged: file is ready to be comitted after adding,
    unmodified: unchangeed
}

Add & Commit:-

add -> adds new or changed files in your working directory to the git staging area ->  git add <file name>

commit ->  it is the record of change ->  git commit -m some message"


Push Command:-

push -> upload local repo content to remote repo -> git push origin main

Init Command:-

init -> used to create a new git repo from locally/initialize git in a local repo

git init
git remote add origin <link>
git remote -v
git branch
git branch -m main
git push origin main/git push -u origin main -> to set origin main as default next time we push


Branch Commands:-

to check branch -> git branch
to rename branch -> git branch -b "<branch name>"
to navigate -> git checkout <branch name>
to delete branch -> git branch -m <branch name>

Merging Code:-

to compare commits, branches, files and more -> git diff <branch name>
git merge <branch name>  
(The rule is: git merge X means "merge branch X into my CURRENT branch.")

OR

create a PR -> A Pull Request (PR) is a GitHub feature that says:

"I've made some changes in my branch. Please review them and merge them into another branch."

It's called a pull request because you're requesting someone to pull your changes into their branch.


Pull Command:-used to fetch and
download content from a remote repo and immediately update local repo to match that content -> git pull origin main

Resolving Merge Cnflicts:-
an event that takes place whengit is unable to automatically resolve differences in code between two commits


Undoing changes:-

case 1: staged changes
git reset <file name>
git reset
-> staged to before add

case 2: committed changes(for one commit)
git reset HEAD~1
-> comitted to before add

case 3: committed changes(for many commits)
git reset <commit hash> -> committed to specified commit
git reset --hard <commit hash> -> undo changes from vscode as well


view logs:- git log


Fork:-

a fork is a new repository that shares code and visibility settings with the original "upstream" repository
fork is a rough copy

write entire process