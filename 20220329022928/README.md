# Having multiple git accounts and pushing code

When using multiple git accounts the best thing to do is create
individual ssh keys for each account and on a per repository basis set
the `git config --local ` configuration of ssh to the required key.

```bash
git config core.sshCommand "ssh -i ~/.ssh/id_rsa_example -F /dev/null"
```
