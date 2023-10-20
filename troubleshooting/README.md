# Troubleshooting

## Push

### Ignore files that had been pushed to the repo
- You need to *untrack* those files (*NOT DELETE THEM*) with 
    ```bash
    git rm --cached filename

    # for a folder
    git rm -r --cached foldername
    ```
- Also remember to add those files to `.gitignore`. You can add them before or after doing untracking stuffs. 
- References: 
    - https://stackoverflow.com/a/1139797 
    - https://gist.github.com/tsrivishnu/a2f3adbbca9fcad5f3597af301ad1abb

## Commit

### Undo the revert
- If you revert a commit in your local repo accidentally, it's recommended to use `git reset` (because that revert commit has not been published) to undo that revert commit
    
    ```bash
    git reset --hard HEAD^
    ```

    or 

    ```bash
    git reset --hard HEAD~1
    ```

    - They both reset to the parent commit of the current commit. Aware that in this scenario, the current commit is the revert commit.
        
        - Note: `HEAD^` and `HEAD~1` is the same. Both of them refers to the parent commit of the current commit.

- If you want to revert a pushed commit, it's recommended to use `git revert` to revert that revert commit

    ```bash
    git revert HEAD
    ```

    This command means we will make a new commit undoing the changes made by the current commit (which is the revert commit)

- Note: to easily distinguish `git reset` & `git revert` in matter of syntax and behavior, just remember that `git reset` will come back to a commit, and `git revert` will undo a commit by making a new commit

### Undo the reset for commited changes
- Commits are kept in reflog for an expiration date. Hence, in case you accidentally reset a commit, you're still able to undo the reset if the commits are still there in the reflog
- Solution: view the commit hash in reflog and reset to that commit

    ```bash
    git reflog

    git reset <commit_hash>
    ```
- Note that, it is recommended to use the same reset mode with the previous reset. Example: at first, you accidentally `git reset --hard HEAD~`. To undo, please use `git reset --hard <commit_hash>`
- Super Tip: If reset is just done, and you just want to undo this reset, you can use `HEAD@{1}` instead of the commit hash. Example for `--mixed` mode:

    ```bash
    git reset HEAD@{1}
    ```

- References: 
    - https://stackoverflow.com/questions/2510276/how-do-i-undo-git-reset
    - https://stackoverflow.com/questions/5473/how-can-i-undo-git-reset-hard-head1

### Undo the reset for unstaged changes
- Create a recovery state for files at the last `git add <file>`
    
    ```bash
    git fsck --cache --no-reflogs --lost-found --dangling HEAD
    ```

- Those recovered files can be found in `.git/lost-found/other`
- References: 
    - https://stackoverflow.com/questions/1108853/recovering-added-staged-file-after-doing-git-reset-hard-head/1109433#1109433

## todo: merge conflict -> this is a very big topic