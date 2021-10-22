# Getting Started

## setup repository

```bash
export PAT=$(cat ~/.pat | base64 --decode) ORG=$(cat ~/.org) PROJECT=$(cat ./project)

##  initialise repository
git init --initial-branch=main
git config --global core.editor "code --wait"
git config --global user.name "Paul Maxfield"
git config --global user.email ${ORG}@users.noreply.dev.azure.com
git add --all
git commit --all --message "initialise repository"

##  push to remote
git remote add origin https://${PAT}@github.com/${ORG}/${PROJECT}.git
git push -u origin --all

##  lazy update
git commit --all --message "update"
git push -u origin --all

##  clean up my lazy updates
git rebase --root -i --force
git push --force
```
