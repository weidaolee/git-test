# git-test
## Setting the SSH connection to github
### 1. Generating ssh key

```
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

### 2. Paste the content in the `id_rsa.pub` file to github [setting](https://github.com/settings/keys) page

```
$ cat ~/.ssh/id_rsa.pub
```

### 3. Add the SSH key to the `ssh-agent`
First start the ssh-agent in the background.

```
$ eval "$(ssh-agent -s)"
```
Then add your SSH private key to the ssh-agent.

```
$ ssh-add ~/.ssh/id_rsa
```

### 4. Test the SSH connection

```
$ ssh -T git@github.com
```
If successed, it will output: `Hi <Github username> You've successfully authenticated, but GitHub does not provide shell access.`

## Configuring GitHub
Setting up the configuration details of the GitHub user

```
$ git init
$ git config --local user.name "<user_name>"
$ git config --local user.email "<email_id>"
```

or for **global**

```
$ git config --global user.name "<user_name>"
$ git config --global user.email "<email_id>"
```

## Commit and push to a repository on github via command lines

```
$ git add README.md
$ git commit -m "first commit"
$ git remote add origin <ssh_target>
$ git push -u origin master
```

## Reference
[Connecting to GitHub with SSH](https://help.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh)
