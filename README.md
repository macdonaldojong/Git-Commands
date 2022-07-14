# Git-Commands

## To create a new repository on the command line
```
git init
git commit -m "first commit"
git branch -M main
git remote add origin <https://github.com/macdonaldojong/test.git>
git push -u origin main
git fetch --all
git pull 
```

![image](https://user-images.githubusercontent.com/58276505/172822039-4959a186-04cb-47a1-82dd-b887e8d576a6.png)

## For push an existing repository from the command line

```
git clone  <https://github.com/macdonaldojong/test.git>

git checkout -b <new-branch>  (create new & change to new branch)

git status		                       	(check modification status)
git add -A 			                      (To add all files in folder)
git commit -m "first commit"
 
git branch		                       	(To check which branch)
git branch -M main      	           (To check which branch)
git checkout <branchname>	          (Switching Branches)
  
git remote add origin <https://github.com/macdonaldojong/test.git>
git fetch --all 		                  (Git Checkout a Remote Branch)

git checkout ＜remotebranch＞        (To checkout a remote branch in another remote-account)
git checkout -b ＜remotebranch＞ origin/＜remotebranch＞ (Create & checkout a remote branch in another remote-account)

git branch main 		                   (confirm branch with remote origin or switch)
git push -u origin main              (origin main or master, always check by running: git branch)

git fetch --all
git pull    		                       (pull any difference in the remote origin)
```

## Revert a just commit/push

Roll back Git to your previous commit without changing the files

```
git reset --mixed origin/master
git add .
git commit -m "This is a new commit for what I originally planned to be an amendmend"
git push origin master


git push --force origin master         # to overide others commits and force yours

# push large files (lfs)
git lfs install              # if not exist
git lfs track "*.psd"        #  psd = is the large file type
git add .gitattributes       # make sure it is tracked

git add file.psd
git commit -m "Add design file"
git push origin main
```

## Git Merge:
  
### Before the merging process we should take some steps.
* Firstly, invoke git status so that to point HEAD to the correct merge-receiving branch. 
* Run git checkout <receiving branch> to switch to the receiving branch.
* The next step is to fetch latest remote commits.
* The receiving branch and the merging branch should be updated with the latest remote changes.
* Invoke git fetch to pull the latest remote commits.
* After the fetching process invoke git pull to update the master branch.
* The final step is executing git merge <branch name> which is the name of the branch to be merged into the receiving branch.

```
git status
git checkout <receiving branch>    (to switch to the receiving branch)
git fetch        		(to pull the latest remote commits)
git pull 			(to update the master branch)
git merge <branch name>
```

### - Fast forward merge
* A fast-forward merge occurs the path from the current branch to the target branch is linear. The fast-forward merge combines the histories, as all the commits that are reachable from the target branch are available through the current branch. Here’s an example of a fast-forward merge:
* A fast-forward merges are used to fix bugs and small features, whereas 3-way merges are used to integrate long-running features. The following examples use a fast-forward merge:

![image](https://user-images.githubusercontent.com/58276505/172824170-323f2466-92f3-4d9c-bd29-186ef60fd1f6.png)

```
# Start the stage
git checkout -b stage master
# Edit some files
git add <file>
git commit -m "Start with the stage"
# Edit some files
git add <file>
git commit -m "Finish with the stage"
# Merge in the stage branch
git checkout master
git merge stage
git branch -d stage
```

### 3-way merge
* A 3-way merge is required when the master branch progresses while the stage is in progress.
* This is used when members of the team work on the large feature simultaneously:

![image](https://user-images.githubusercontent.com/58276505/172825361-a0f3497f-cfca-4aa4-8f66-33e9caa0a5ae.png)

```
# Start the stage
git checkout -b stage master
# Edit some files
git add <file>
git commit -m "Start with the stage"
# Edit some files
git add <file>
git commit -m "Finish with the stage"
# Develop the master branch
git checkout master
# Edit some files
git add <file>
git commit -m "Make some super-stable changes to master"
# Merge in the stage branch
git merge stage
git branch -d stage
```

https://www.w3docs.com/learn-git/git-merge.html

NB: Always check official Doc here: https://git-scm.com/docs/git-add
