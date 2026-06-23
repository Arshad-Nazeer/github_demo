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