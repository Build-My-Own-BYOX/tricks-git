# Tricks

1. Push an empty folder
- Git will ignore empty folder when we're pushing to a repo. Hence, we can put anything inside that folder to make sure it appears in the remote repo
- Some convention for that "anything" would be ".gitkeep" or ".keep"
- Example

    ```
    ---folder A
    |
    -----.gitkeep
    ```
- References: https://www.freecodecamp.org/news/what-is-gitkeep/

2. Edit the latest commit message
- Use command `git commit --amend -m "New commit message"`
- Reference: https://linuxize.com/post/change-git-commit-message/

3. Edit the latest commit message that had been pushed
- Need to force push after amending the commit `git push --force <remoteName> <branchName>`
- Reference: https://linuxize.com/post/change-git-commit-message/

4. Run test before pushing
- Use `pre-push GIT HOOKS`. 
- Example: Write test command to the file `.git/hooks/pre-push`
- However, a better practice would be use `pre-commit`, which is running hooks before committing
- For more detail, visit [here](../terms/githooks.md)
- Reference: 
    - `pre-push`: https://benfrain.com/a-git-pre-push-hook-to-run-tests-on-a-particular-branch-when-you-push/
    - `pre-commit`: https://blog.devgenius.io/automate-unit-tests-before-each-commit-by-git-hook-f331f0499786
- Notes: team should not rely comprehensively on githooks because: 
    - Really easy to bypass githooks with `--no-verify`
    - githooks stay in `.git`, which is not shared between teams
    - Enforcement should come from the remote repository
- Alternative for `githooks` is finding [support from IDE](https://www.jetbrains.com/go/guide/tips/vcs-run-tests-before-commit/)

5. Skip git hooks when committing/pushing
- Use `--no-verify`
- Example
    - Skip `pre-commit`:
        ```bash
        git commit --no-verify -m "commit message"
        ```
    
    - Skip `pre-push`:
        ```bash
        git push --no-verify
        ```
- However, some commands such as `cherry-pick` does not support `--no-verify`. The easiest bypass solution is to comment those hooks temporarily.
- Reference: https://stackoverflow.com/questions/7230820/skip-git-commit-hooks

6. Share git hooks with team
- Reason: git hooks stay in `.git`, hence not pushed to remote repositoyr -> got to find a workaround to share these hooks with team
- Solution: create a folder called `scripts` or `.githooks` or `git-scripts` (or any name you want) in your local repo, and use
    - [RECOMMEND] config hooks path with 

        ```bash
        git config core.hooksPath <folder_name>
        ```

    - setup symlinks 

        ```bash
        ln -s <folder_name> ".git/hooks"
        ```
- Put any githook setup to a script and ask your team to run it. Example:

    ```bash
    #!/bin/bash

    git config core.hooksPath <folder_name>
    ```
- Reference: 
    - https://stackoverflow.com/a/37861972

7. Better commit message
- Use gitmoji: https://github.com/carloscuesta/gitmoji
    - Example: use vscode extension: https://github.com/seatonjiang/gitmoji-vscode
- Rules for writing good commit message:
    - write as giving order: start the sentence with verb
    - prefix with commit type, e.g., Bugfix, Update
    - NO filler words, e.g., I think
- Answer these questions when writing commit:
    - Why is these changes needed?
    - What are the changes in reference to?
- Some recommended commit types:
    - feat: new feature
    - fix: bug fix
    - refactor: clean & refactor code
    - docs: add/update documentation
    - test: add/update tests
    - perf: improve performance
    - ci: CI/CD related
- Examples of good commit message: 
    - feat: improve performance with lazy load implementation for images
    - fix: bug preventing users from submitting the subscribe form
- Examples of bad commit message:
    - fixed bug on landing page
    - oops
    - tmp
    - test
- Reference: https://www.freecodecamp.org/news/how-to-write-better-git-commit-messages/

8. Revert the last commit
- Use `reset`

    ```bash
    git reset --soft HEAD~1
    ```
- Add alias by writing to `~/.gitconfig`
    ```
    [alias]
        undo = reset --soft HEAD~1
    ```

    Then you can use `git undo` everywhere in your machine.

- Reference: https://dev.to/isabelcmdcosta/how-to-undo-the-last-commit--31mg#comment-2bo1


10000. todo: 
- cherry pick
