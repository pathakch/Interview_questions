#### GIT Commands

1. `git branch -v`: shows branch name,last commit hash and commit messages
2. `git branch --merged`: shows which branches has been merged 
3. `git branch --no-merged`: shows which branches have not been merged
4. `git branch -d branch_name`: deletes given branch  
5. `rm -rf .git`: removes .git file from a folder so that the folder will not remain git repository.
6. `git remote`: to check whether we are on remote directory or not 
7. `git remote -v`: to check whether we are on remote directory or not
8. `git remote add origin {remote_repo_url}`:
9. `git remote set-url origin {remote_repo_url}` : To set remote origin even though you are on different remote origin, it sill set remote origin to the new url and after pushing code it will be updated to new remote origin means to new remote repo.

`git remote -v`
  - origin  https://github.com/pathakch/Sample_Repo.git (fetch)
  - origin  https://github.com/pathakch/Sample_Repo.git (push)

9. `git push origin branch_name(bugfix)` : pushesh the new branch on remote git repo.
10. `git push origin bugfix:mybugfix`  => will push new branch named bugfix with a different name "mybugfix"
11. `git push -d origin branch_name` : deletes branches from remote  repository
12. `git merge branch_name` : merge other branches with master(give this command when u r on master branch but, not necessary,i think)

Scenario:1. 
  - suppose we created a repo 'test_repo' with the help of another repo as template, we made some changes in 'test_repo' 
but now we want to delete those commit history and update this repo with the template repo, Follow below steps.
---------------------------------------------------------------------------------------------------------------------------------
    Step.1 set template repo as upstream <git remote add upstream {remote_repo_url}>
    Step.2 fetch latest template repo <git fetch upstream>
    Step.3 Merge main branch of template repo into our 'test_repo'<git merge upstream/main>
    Step.4 run <git merge upstream/main --allow-unrelated-histories>
--------------------------------------------------------------------------------------------------------------------------------


Scenario:2. 
- Delete an old commit from main branch or from any branch.Ex:(a->b->c->d) delete commit b ,result should be (a->c->d)
--------------------------------------------------------------------------------------------------------------------------------
    if we have 
    commit-1
    commit-2
    commit-3
    and i want to delete commit-2 
    then follow below steps
    step. 1. git rebase -i commit-1 (this is the commit before the deleting commit-2)
    step. 2. write 'drop' before commit-2 (in VIM file which will be opened after running step.1, we can write edit also, which will allow to edit any line of code in any file belonging to that commit, it won't delete the commit)
    step. 3. add any additional files (manually) if required and stage them running <git add file_name>
    step. 3. run command git rebase --continue (which will apply all the remainig commits like commit-3 in above case)
    step. 4 git push -f origin (force push to the branch and it will rewrite old history, force rewrite old history.)
---------------------------------------------------------------------------------------------------------------

Scenario:3. 
- Delete all the commits from a branch and push a fresh commit which will delete all the history also
---------------------------------------------------------------------------------------------------------------
    if we want to delete all the comit from branch ABC.
    step 1. Be on branch ABC and create an orphan branch <git checkout --orphan new_branch> this branch will not have any commit but it will have all the files from the base branch like any other feature branch 
    step 2. delete all the files from this branch if not required, do not delete files if required and need to make chages in those existing files or create any other file manually if required.
    step 3. stage if any files created in step 2 <git add file_name>
    step 4. run <git branch -M new_branch> this will rename our 'new_branch' as branch 'ABC' 
    step 5. <git commit -m"">
    step 6. run <git push -f origin ABC> which wil push this latest change and only one fresh commit to branch 'ABC'

---------------------------------------------------------------------------------------------
- Command to push an empty commit to github to run cicd in github action
    - `git commit --allow-empty -m"trigger ci cd"` 
---------------------------------------------------------------------------------------------

