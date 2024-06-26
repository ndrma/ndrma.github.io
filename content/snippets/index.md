+++
title = 'Snippets'
date = 2024-04-07T00:17:30+01:00
draft = false
+++

second
```
asdasd

```

## github repos


basics

```
optional: mkdir #### && cd ####

git init (-b main (if that's the branch))
git remote add origin [GITHUB SSH LINK TO REPO]
git add . (or whatever you want added)
git commit - m "commit of doom"
git push (-u) origin main

# can verify if the remote url was set correctly with: git remote -v

sometimes it might glitch still, check with git show-ref what the head 
is then change with git push origin HEAD:master or main

```
## more git stuff
```
git add -p specificfile.md
git commit -m "lalalal"

#create a graph to show shit regarding git with:
git log --graph --decorate --abbrev-commit --all --pretty=oneline
```
{{< line_break >}}
Extra info here: http://longair.net/blog/2009/04/16/git-fetch-and-merge/ and [here](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-branches#about-the-default-branch).


## zoxide bash add that I always forget

walkthrough [here](https://www.youtube.com/watch?v=aghxkpyRVDY)

```
#zoxide change z to cd and activate
eval "$(zoxide init --cmd cd bash)"
```

