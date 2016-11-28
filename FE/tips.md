#CSS

 - Float elements are aligned to top.


#GIT

 - To fix detached head problem
 1. Create a branch that points to the detached HEAD
 
 `git checkout -b temp`
 
 This will reattach your HEAD to the new `temp` branch
 2. Next, compare the current commit, with the normal branch on which you expected to be working
 
 `git diff qa temp`
 
 `git diff origin/qa temp`
 
 3. Then, update `qa` to point to it
 
 `git branch -f qa temp`
 
 `git checkout qa`
 
 4. Delete the temporary branch
 
 `git branch -d temp`
