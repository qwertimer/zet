# Useful curl Note - Getting the latest version number from a github project

If we need to find the latest version of any project we can use curl and jq to check for the latest

```bash
curl -sSL https://api.github.com/repos/<package>/releases/latest | jq -r .name
```
