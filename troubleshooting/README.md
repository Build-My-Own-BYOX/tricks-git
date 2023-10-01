# Troubleshooting

1. Troubleshooting: Ignore files that had been pushed to the repo
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

2. todo: merge conflict -> this is a very big topic
