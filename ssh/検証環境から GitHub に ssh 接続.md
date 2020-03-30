```
$ ssh-keygen -f ~/.ssh/repo_name
$ vi ~/.ssh/config

Host repo_name
  HostName github.com
  IdentityFile ~/.ssh/repo_name
  User git

$ git clone repo_name:xxx/xxxx.git
```
