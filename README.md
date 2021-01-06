Github Packages now supports Docker Registry

One of the easiest way to setup your own Docker Registry is by using Github Packages.

Docker Registry in Github is also convenient. Having the Docker Images close to where you are storing your code allows for better developer productivity.

However setting up your first Docker Registry using Github Packages is not very well documented in my opinion. Here’s my attempt to simplify your initial setup and save you time. Read until the end for common errors and how to troubleshoot.

TLDR; Fix Docker Rate Limit issues by using Github Packages

Steps

1. Create a Github Repo where you will store your docker image / Alternatively use an existing Github Repo.


![create](images/1*uXkrbVgP0fX1kHQv2i8gsg.png)

2. Create a github token in https://github.com/settings/tokens


![token](images/1*-ZixXQc9JHISIIH3uaB3qg.png)


3. Setup your github token with write:packages repo and optionally delete:packages if you need it to automatically delete packages

![ww](images/1*NZzROynLn1XzfwTzVYaV2g.png)


4. Setup your .bashrc or .zshrc with environment variables or (export them manually)
```
export GITHUB_USER=kenichi-shibata
export GITHUB_TOKEN_RWD=<your newly generated token>
```

Login to github’s docker registry
```
❯ echo $GITHUB_TOKEN_RWD | docker login https://docker.pkg.github.com -u ${GITHUB_USER} --password-stdin

WARNING! Your password will be stored unencrypted in /Users/kenichishibata/.docker/config.json.
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credentials-store

Login Succeeded
```

