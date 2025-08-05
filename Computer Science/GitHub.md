# Starting a New Project

On Github, click + (Create) > New Repository
![[Pasted image 20231219111327.png]]

Now, we have to enter in the details about our repository, including
- Template
- Owner
- Name
- Description
- Access Rights
- Starting Files

![[Pasted image 20231219111540.png]]

## Templates
I never use these, but they seem to be a way to set standards throughout multiple repositories.

## Owner and Repository Name
Here, you set the name of the repository, as well as who has admin rights for it. 
==Note: The name is not expected to be unique across Github.==

## Description
While the description is optional, it is good practice, particularly if the name is not descriptive. You never know who is going to be looking at these repositories, so try and make it as easy for them to understand as possible. 

## Access Rights
Github is publicly hosted, but your repository does not need to be. You can set whether your repository is publicly viewable or not. If you are planning on keeping your code confidential, there may be extra fees to host on Github.

## Starting Files
The rest of this has to do with starting with files. A blank repository is perfectly fine for most projects, but these are some of the most common files amongst repositories.

### README File
The most common initial file is a README. Selecting "Add a README file" will create one in the repository root directory. This file is nearly always the first point-of-contact for a newcomer to your repository. If they download your repository, this is the most obvious file to read first, and if you are hosting on Github, this file is what gets rendered under the file list when people view your repository. 

==The README file is assumed to be Markdown when rendered.==

In general, there are things that your README is expected to contain:
- What problem the project solves
- High-level explanation of how the project works
- Contribution expectations:
	- Is the project open to contributions from others?
	- If so, what is the process for doing so?
	- Are there any formatting requirements?
	- Is there a bug tracker of any kind that contributors should watch?

==Note that while having the README in your directory root is default behavior, Github will still find it if you put it in your repositories .github folder, or even a "docs" folder.==

If you have more questions about the README file, be sure to [read this page](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-readmes), but keep in mind that README files should be limited in scope, and [extra information should be in a wiki](https://docs.github.com/en/communities/documenting-your-project-with-wikis/about-wikis).

### .gitignore File
The .gitignore file is a hidden file intended to keep rules for [what files should be ignored when using git](https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files). It supports asterisks (\*) as wildcards, and you can hide folders, specific files, files of a type, and anything that matches a naming rule. These are commonly used for compilation files in code repositories and private files in content repositories. 

The .gitignore template list shows common ignore rules for repositories of different languages, like hiding \*.o files for C++.

If you later realize that a file in your repository would have been better ignored, then you have to ==remove the file from the tracking cache before adding a .gitignore rule==:
```shell
git rm --cached FILENAME
```

### License Files
Github is used for many Open Source projects, allowing contributors to create and maintain projects for the greater good. With that in mind, they make it easy to declare the license of your repository. The license determines who has the rights to the code, whether it can be reproduced, distributed, or whether someone can create derivative works.  

When creating a Github repository, you can automatically add a LICENSE.txt file to the directory root. The list contains many of the common licenses and having this file allows people using the search bar on Github to find your project when they search by license.

While most projects have a LICENSE file that contains info regarding their license, ==a repository with no license file retains all copyrights==, meaning only the sole creator has rights to the code. 

Many licenses [serve a specific purpose](https://choosealicense.com/). If you are doing things purely for education, you may want the MIT license, which gives everything out for free. If you want the programmer community to be able to help maintain something you compile, you might check out the GNU license. The choice is yours. 

# SSH

I highly suggest [setting up an SSH key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account) for grabbing your github repositories. It is more secure and easier to use. 

First, make sure you have git-bash installed. Then, run the following command, replacing the example with your email: 
```shell
ssh-keygen -t ed25519 -C "your_email@example.com"
```
You will then be asked to define a filename for the key. It doesn't actually matter, but I do suggest the default. Then, you will put in a password, or just hit enter for no password.

This, if done with defaults, will create a set of files in C:/Users/(you)/.ssh called "id_ed25519", and "id_ed25519.pub". The file without an extension is your Private Key, which still needs to be registered with your ssh agent, so go ahead and run the following in an admin shell: 
```powershell
ssh-add /c/Users/YOU/.ssh/id_ed25519
```

Now, your ssh Private Key is registered on your local machine. The final step in the process is to register the Public Key with Github. Your public key is the content of the \*.pub file created earlier, so go ahead and copy the contents of that file to your clipboard: 
```shell
$ clip < ~/.ssh/id_ed25519.pub
```
Open up Github in the browser and sign in if you aren't already. Go to Settings > SSH and GPG Keys, and click the Add SSH Key button. You will be asked for a title, a type, and the key itself. The title should refer to the device you generated the key on, type should be for Authorization, and the key is the contents of the file we made earlier, that should be still in our clipboard. Once you click Add Key, you will be all set to start using SSH for communicating with Github.

## Pulling down a repository

Once you have a repository instantiated on Github, it is time to **clone** it, or copy it to your local machine. 

Go to your repository page on Github. 
![[Pasted image 20231219143818.png]]
Click the Code button and select SSH. Then press the the button showing two windows (Labeled "Copy url to clipboard").
![[Pasted image 20231219144004.png]]
Open a terminal to a directory to store your git repositories in. This parent directory will have folders inside it for each repository. then run:
```shell
git clone [COPIED_TEXT]
```
You will be asked for your password, then it will clone the repository to that directory.
![[Pasted image 20231219144655.png]]

You can now drop into the folder that was created and run `git status`.
![[Pasted image 20231219144854.png]]
Running status will show you which **Branch** you're local directory is set to, as well as how up-to-date the local version is with the remote repository. 

### Branches
Each repository can have several branches. These are parallel versions of the repository that you can work on independently, then **Merge** into each other. A fresh repository starts with the "main" branch, but the standard is to have a branch for the current complete version, and a separate branch for big revisions or new functionality. Lets create a "working" branch by running:
```shell
git checkout -b "working"
git push --set-upstream origin working
```
The checkout line creates a local branch called working, then switches to it.
The push sends the information to Github that we have made this branch.
![[Pasted image 20231219145848.png]]

### Saving your changes

As you make changes to the local repository, you will need to **add** files so that we can track them, then **commit** changes, which organizes all the changes to the currently tracked files into a segment of git data. Finally, you will have to **push** the commits to the remote repository. 

In my example, I am on the working branch and I have changed the README file and added a python file, which is incomplete. As such I want to commit the README, but not the python file. First I always check on things by running git status.

![[Pasted image 20231219151200.png]]

We now can see that the README file has been changed, but that .idea and propertyfiller are not being tracked. First, add the changes from README.
```shell
git add README.md
```

![[Pasted image 20231219151413.png]]

The green text means that those changes are staged for commit, so we can...
```shell
git commit -m "12/19/23 Added authorship to README (WP)"
```

![[Pasted image 20231219151525.png]]

A note about committing: I've seen commit messages formatted a lot of ways, but generally, the main line is the commit title, then you can add a new line and go into more depth. I personally prefer "\[date\] \[summary\] (\[initials\])" as the entirety of my commit messages, but this may change when I start using git more heavily.

![[Pasted image 20231219152314.png]]

If you run status after a commit, you can see that status notifies you about it. Lets go ahead and push our changes
```shell
git push
```

![[Pasted image 20231219152635.png]]

Once your 