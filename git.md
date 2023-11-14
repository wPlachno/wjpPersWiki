# Git 

Git is source control, a system for tracking changes to code, while Github is a company which provides servers for hosting git repositories.

## Quick Summary

To use git, you need to understand the general idea of how it works. The first thing you'll need to worry about is your upstream, or your **origin**, or the remote server where your repo will be hosted. You also have a local directory, or **working directory**, where you will interact with a local version of the repo. As you work on the files, you will need to **"stage"** them, or prepare them to be added to a commit, then **"commit"** them, or bundle up all the changes into one piece. Once you have your commits ready, you can **"push"** them to the remote repo, transmitting the changes and incorporating them into your remote code. There's a [pretty great writeup by Cosima Meyer](https://cosimameyer.com/post/git-the-perks-of-collaboration-and-version-control/) on how to connect git with the RStudio IDE that has some charts that may help.

On top of all of this, there is also the idea of branches.

## Commands

The following is a list of very common git use cases and the command line arguments to deal with them.

### Instantiating a git repo on Github

Github makes it easy to host a repo. Just log in, and add a new repository. My suggestion is to always do blank projects and add as you go, including a README.md, which is the main thing someone will see if they visit your repository on the Github web app.

The process of actually making a github repository is relatively simple. If you go through the website, it's just a matter of following the steps, picking a name, picking what items to have in the repo already, and choosing a distribution license. Then, you can find the repo page on github, click the `code` button, and copy the upstream SSH link.

In the command line, navigate to where you want your repo to sit locally. If you haven't already, you'll need to setup the local directory as a git-tracked directory, 
```
git init -b main
``` 
To link the local git with the upstream repository you created, use the command:
```
# Replace REMOTE-URL with the ssh link from earlier
git remote add origin REMOTE-URL 
```
You can verify using `git remote -v`.

Note: If your repo was instantiated with any files, you will want to move them to your local host with a `git pull origin main` before any `git add` or `git commit`. During your first push, you'll want to use the verbose `git push --set-upstream origin main`

If you dont want to use the Github interface, you can use Github CLI, and activate the `gh repo create` command. 

### Command List

```
# Initialize a local directory as a git repo on the main branch
git init -b main

# To set the upstream url
git remote add origin REMOTE-URL

# To see where your upstream is
git remote -v

# To double check that your working directory has the latest changes from the origin
git pull

# To see the current status of your local version
git status

# To stage a file to a commit, though you can use * to do all files
git add FILENAME

# To make a local commit, using my personal standard format for commit messages
git commit -m "DATE COMMIT_SUMMARY (YOUR_INITIALS)"

# To move all local commits upstream
git push

```