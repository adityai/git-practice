### Display git version

```
git --version

```

### Git config

```
git config --global user.name "adityai"
git config --global user.email "adityaii@gmail.com"
git config --global color.ui "auto"
```

### Initialize a git repo

```
// Create a new directory
mkdir app
cd app/

// Initialize git repo
git init 

// Create a blank README.md file
touch README.md

// Git add all 
git add *

// Commit with message
git commit -m "Initial commit"

// Add git remote repo
git remote add origin https://github.com/adityai/git-tutorial.git

// Git push to master
git push -u origin master
```

### Add folders and files 

```
mkdir src/test/resources -p
touch src/test/resources/testData.csv
git add *
git commit -m "Adding src test resources tesdData.csv"
git push -u origin master

// Create a temp file to delete from the repo later
touch tempFileToDelete.txt
git add *
git commit -m "Adding tempFileToDelete.txt"
git push -u origin master

// Create a file to move within the repo later
touch testFileToMoveUsingGit.txt
git add *
git commit -m "Adding testFileToMoveUsingGit.txt"
git push -u origin master

// Delete a file from repo
git rm tempFileToDelete.txt 
git commit -m "Deleting testFileToDelete.txt"
git push -u origin master

// Move a file within the repo
git mv testFileToMoveUsingGit.txt src/test/resources renamedTestFileToMoveUsingGit.txt
git commit -m "Moved testFileToMoveUsingGit.txt to src/test/resources/renamedTestFileToMoveUsingGit.txt"
git push -u origin master
```

### Branching
```
mkdir app1
cd app1/

// Clone the repo
git clone https://github.com/adityai/git-tutorial.git
cd git-tutorial/

// Check which branch local is pointing to
git branch

// Create a new branch
git branch branch1

// Switch to the new branch
git checkout branch1

// Create a blank file to merge later with master
touch testFileAddedInBranch_1.txt
git add *
git commit -m "Added testFileAddedInBranch_1.txt"
git push -u origin branch1

//Simple merge
git checkout master
git merge branch1
git push -u origin master

//Delete remote branch
git checkout branch1
git push origin --delete branch1

// Add a file in the master
git checkout master
touch testFileAddedInMaster.txt
git add *
git commit -m "Test file added in master"
git push -u origin master
```

### Merge simple text changes 
```
git checkout branch2
echo "Adding text in branch2" > testFileAddedInBranch_1.txt
git add *
git commit -m "Adding text in testFileAddedInBranch_1.txt in branch2"
git status
git push -u origin branch2

// Add different text in the same file in the master
git checkout master
echo "Text added to file in master." > testFileAddedInBranch_1.txt
git add *
git commit -m "Added text in testFileAddedInBranch_1.txt in master"
git push -u origin master

// Try a merge
git checkout master
git merge branch2

// Observe the output of the previous command
// CONFLICT (content): Merge conflict in testFileAddedInBranch_1.txt
// Automatic merge failed; fix conflicts and then commit the result.

// Edit the testFileAddedInBranch_1.txt 
// Fix all the merge issues and push to master
git push -u origin master


