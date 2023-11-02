# security
- Focus on practices on securing repository, safely downloading and running project

## Secret Management

### Detect secret 
- Use gitleaks
    ```bash 
    gitleaks detect --source . -v
    ```
    

### Removing sensitive data from a repository
- Use bfg 
    ```bash
    bfg --delete-files YOUR-FILE-WITH-SENSITIVE-DATA
    ```
    Then `git push --force`
- References: 
    - https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository