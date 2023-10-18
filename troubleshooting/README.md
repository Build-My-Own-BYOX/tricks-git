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

    This command means we will make a new commit undo the changes made by the current commit (which is the revert commit)

- Note: to easily distinguish `git reset` & `git revert` in matter of syntax and behavior, just remember that `git reset` will come back to a commit, and `git revert` will undo a commit by making a new commit

### Undo the reset

## todo: merge conflict -> this is a very big topic