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

4. todo: githooks

5. todo: revert a pushed commit

6. todo: cherry pick
