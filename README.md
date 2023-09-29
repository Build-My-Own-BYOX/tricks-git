# tricks-git
A collection of tricks, debug, lessons that I learn about git through out my adventure (and it's still going)

Tips: Each heading will be divided to certain categories: tricks, troubleshooting, lessons, common "good/bad" pratices.

And, mostly the title of each item would be kept as clean as possible, such that you can google search for the essential info with that title

And (again), this repo focuses on providing quick look, not a wikipedia with long explanation. Hope you enjoy the dessert.

1. Tricks: Push an empty folder
- Git will ignore empty folder when we're pushing to a repo. Hence, we can put anything inside that folder to make sure it appears in the remote repo
- Some convention for that "anything" would be ".gitkeep" or ".keep"
- Example

    ```
    ---folder A
    |
    -----.gitkeep
    ```
- References: https://www.freecodecamp.org/news/what-is-gitkeep/

2. Troubleshooting: Ignore files that had been pushed to the repo
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

3. todo: git stash

4. todo: merge conflict -> this is a very big topic

5. todo: ssh keys & control multiple ssh keys

6. todo: edit a commit message

7. todo: revert a pushed commit

8. todo: cherry pick

9. todo: githooks


## TODO: place categories into folders