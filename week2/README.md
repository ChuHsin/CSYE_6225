# Week 2

## TEST
Why Test?
* reduce bugs
* tests service as good documentation
* allow for safe refactoring
* reduce the cost of making code changes
* allow you to deliver code with confidence
---
### Unit Tests
#### What is Unit Test
* Unit tests should not require access to any external systems such as network, databases
* all external systems such as database, file server, etc, are mocked out using specific test APIs and test data.
* 模拟所有系统外的东西，
* isolate parts of programs
* verify that independent part of programs are working correctly
* fast and reliable
* drawbacks
  * take time to bild
  * require maintenance
* an incorrect unit test can let bug go thru unnoticed for long time
* **Test always take longer than the code itself.**
---
### Integration Test
Integration tests verify that interaction between multiple components(applications, services, modules, etc.) is working as expected.
#### Challenges
* difficult to test all critical paths
* hard to find the source of errors
* requires time and commitment from multiple component owners

### Performance/Load/Stress Testing
* Simulate a heavy load on a server, network or object to test its strength or to analyze overall performance under different load types.
* Load testing is also a way to perform a functional test on websites, databases, LDAPS, webservices, etc.
  
right size for the file, you can do capacity planning without having an environment.

## Version Control
 
Distributed Version Control Systems
* git
* mercurial
* bazaar
* darcs

 distributed version control systems were not proprietary

CVS, SVN tracking changes w/differences, process become slower and slower
Git tracking changes w/Snapshots
when you compare for diff they compute delta of the files 

### Git Has Integrity
* Everything in Git is check-summed before it is stored and is then referred to by that checksum (加和验证) you cannot change file without git finding out.
* Git uses SHA-1 hash, 40-character string composed of hexadecimal characters 0-9 a-f, calculated based on the contents of a file or directory structure in Git.
* Git stores everything in its database not by file name but by the hash value of its contents which means you will see these hash values all over the place.

### Local Git Workflow
* modify files in your working tree.
* stage the files, adding snapshots of them to your staging area.
* do a commit, which takes the files as they are in the staging area and stores that snapshot permanently to your Git directory.
  
### Cloning an Existing Repo
you can clone git repo using either git(SSH) or https transfer protocol, git protocol is recommend to use wherever possible.

### Git Status command

use `git status` everytime before you commit or stage anything


`git add -A`  "add all new files"

`git remote add <url>`

for most of people the **pointer** will be set up is origin - origin is just a alias, it's not required.
"I remove origin as soon as a clone repository and I usually replace it with my first name"

showing your remotes
git remote -v "show you which remote server you have configured"

### Fetching and Pulling from your remotes
* to get data(changes) from remote project, you can use `git fetch` or `git pull` command
* `git fetch` only downloads the data to your local repository - it doesn't automatically merge it with any of your work or modify what you're currently working on. You have to merge it manually into your work when you're ready.
* git pull automatically fetch and then merge that remote branch into your current branch

### Pushing to Remotes
`git push [remote-name] [branch-name]`

`git push origin main`

### Git Branches

organization

then fork to your personal repo


## CI Continuous Integration
practivce of merging all developer working copies to a shared mainline several times a day.
the main aim of CI is to prevent integration problems, referred to as "integration hell".
* is intended to be used in combination with automated unit tests written through the practices of test-driven development.

### GitHub Action


---

10004  git clone git@github.com:bh7cw/webapp-1.git
10005  ls
10006  cd webapp-1
10007  ls
10008  ls -la
10009  ls
10010  git remote -v
10011  git remote add upstream git@github.com:beyond-the-cloud/webapp.git
10012  git remote -v
10013  ls
10014  vi README.md
10015  cd ..
10016  ls
10017  cd webapp-1
10018  ls
10019  git remote -v
10020  git remote add jing git@github.com:beyond-the-cloud/webapp.git
10021  git remote -v
10022  git remote remove jing
10023  git remote -v
10024  ls
10025  vi README.md
10026  ls
10027  cat README.md
10028  git add .
10029  git status
10030  git commit -m "update readme"
10031  git status
10032  git log
10033  git reset --hard
10034  git log
10035  git checkout -b a1
10036  git branch
10037  git log
10038  git push origin a1
10039  git checkout master
10040  git pull upstream master
10041  git push origin master
10042  git checkout a1
10043  git pull origin master
10044  git push origin a1