# Git 101

> "What is this Git thing all about ..?"
>
>> *Awareness is the greatest agent for change* <sub>Eckhart Tolle</sub>

1. [Git in Visual Studio](#vs)
2. [Git in Git Bash](#bash)
3. [Staging the File](#staging)
4. [Commiting the File](#commit)
5. [Pushing the File](#push)
6. [Forking a Repository](#fork)
7. [Git pull request workflow](#pr)

## Git?
[Git](https://git-scm.com) is a version control system (VCS), which allows you to keep track of changes in files. It also coordinates the files and their changes among multiple people - a project team for example - or simply for yourself. Have a look at the [Pro Git](https://git-scm.com/book/en/v2) (Chacon and Straub, 2014) book to lift the lid on Git features.

Git is [widely used](https://en.wikipedia.org/wiki/Git) in industry as a VCS, and as such can be an essential skill to learn as part of your University studies. Many [existing](https://git-scm.com/book/en/v2/Appendix-A%3A-Git-in-Other-Environments-Graphical-Interfaces) coding tools have built-in Git extensions - including Visual Studio. These allow you to easily link your code project, Git and your chosen IDE.

Within Git, the files for each project that you create are collected together in a repository, or 'repo'. On your local computer, the project will contain a ```.git/``` folder containing all the information related to the files in the project, any changes over time, etc. If you delete this folder, your project is no longer considered a Git repo on your local computer.

The basic structure comprises of a 'local repository' which is on your computer, and this is linked to a 'remote repository' on Github. There are, in fact, four distinct that your files need to pass though:
1. The 'Working Directory'
2. The 'Staging Area'
3. The 'Local Repository'
4. The 'Remote Repository'

Everything you may do with Git involving moving files from your computer to a remote repository, and 'cloning' or downloading them from the remote to your computer, will involve moving between these four areas. 

 If you haven't already, create an account at [github.com](https://github.com)

## Getting Started
Also, if you haven't already, download and install Git for your OS from [here](https://git-scm.com/download/). Accept all default options. '```Git Bash Here```' should now be a context menu (right click in Windows) option.

You can create a repo and interact with Git in a number of ways - through an IDE such as Visual Studio, or manually.

<a name="vs"></a>
#### Git in Visual Studio

Look [here](https://devblogs.microsoft.com/visualstudio/improved-git-experience-in-visual-studio-2019/) and [here](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Git-Fundamentals) for information on the latest Git for Visual Studio developments (as of April 2020) and more tutorials. 

*To 'clone' or download a remote repository and open it in Visual Studio:*

```File > Clone or Checkout Code```

In the Github repo, see the green ```Clone or download``` button? Press this button, and the URL you see is the repository location. Copy and paste this into the ```Repository location``` field in Visual Studio.

*To add an existing project in Visual Studio to a version control system, such as Git:* 

With the project open, in the IDE, click ```Add to Source Control``` in the bottom right of the window, and then paste in your remote Git repository address. Click ```Publish``` and then you should see your project as a repo on Github.

<a name="bash"></a>
 #### Git using Git bash

 Have a look at [this](https://www.atlassian.com/git/tutorials/git-bash) for more information on Git bash.

Create a new folder to hold your repository files. Then, right click on this folder - you should have the option ```Git Bash Here``` (if not, make sure you have Git installed on your computer, and you have selected the 'Windows Explorer integration' during the install process).

When you select ```Git Bash Here```, a Git Bash window will open, with it being located inside the folder. Now, you need to initialise this folder as a local repository. At the prompt, enter (the '$' is the prompt):

```bash
$git init
```
You should then see confirmation that this folder is now a Git repository. If you also look in the folder, you should see a ```.git/``` folder containing all of the repository information for Git. 

We have an empty directory, lets add a file. At the prompt, enter:

```bash
$touch file.txt
```
This will create a new, empty file for us, called ```file.txt``` (there are loads of other ways to create a file). This file is in our 'working directory'. We need to move it to the 'staging area' (files to be moved into a local and remote repository need to be 'staged' first, i.e., they need to be prepared or highlighted for 'commiting').

<a name="staging"></a>
##### Staging the file 

By adding this file to the staging area, it becomes 'tracked'. That is, Git starts monitoring it for changes, and it is ready for 'commiting' to your local repository. To do this, we use the '```add```' command in Git:

```bash 
#[adds 'file.txt' to the staging area]
$git add file.txt
```       
```bash
#[add all files in the working directory to the staging area - note the '.']
$git add .              
```
There are other versions of the ```add``` command, but these will be good for now.

You can check which files are in the staging area, by using the ```status``` command:

```bash
$git status
```
You should see an output like this, showing that ```file.txt``` is staged.
![git status 01](./images/01.jpg)

If you edit ```file.txt``` to change it, and then do a ```$git status``` again, you should then see:
![git status 02](./images/02.jpg)

This now shows there are two versions of ```file.txt``` - a tracked and untracked version. To apply the changes to the tracked version, do the ```$git add file.txt``` (or ```$git add .```) again.

<a name="commit"></a>
##### Commiting the file to the Local Repository

We now need to move, or 'commit' or file to our local repository. We do this by using the 'commit' command:

```bash
#[commits 'file.txt' to our local repository]
$git commit -m 'initial commit'
```

The 'commit' command takes all the files which are in the staging area (i.e. which are being tracked) and moves them to the local repository. The ```-m``` switch means that the ```commit``` command will be followed by a commit message (the text between the ' 's). 

You need to write a commit message each time - to remind yourself and others what you did in thet particular commit. See [this](https://chris.beams.io/posts/git-commit/) for guidelines on writing commit messages, and [this](http://whatthecommit.com/) for when you can't think of a message for your commit.

See the 'log' to show each commit you have made to this local repository:

```bash
#[view the commit history]
$git log
```
Have a look [here](https://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History) for more information on the ```log``` command.

<a name="push"></a>
##### Pushing the file to the Remote Repository

First we need to create a Github repository (unless you have already created one). Then we need to add it as a 'remote repository' on our local computer:

```bash
$git remote add origin <your git repo address>
```
For example, it might look like:

```bash
$git remote add origin https://github.com/markdoughty/CSharp-Book.git
```

What does this mean? '```remote```' is a command which ```adds``` a repository address, and calls it ```origin```. 

Now, you need copy your local repository up to the remote repository (i.e. the 'origin'):

```bash
$git push origin master
```

What does this mean? ```push``` is a git command which takes the ```master``` (i.e. the main) branch of your local repository and pushes, or copies it to the ```origin``` remote (i.e. the one you set earlier).

<a name="fork"></a>
##### Forking a Repository

A ```fork``` is a copy of a repository that allows you to experiment with changes without affecting the original project. A forked repository differs from a clone in that a connection exists between your fork and the original repository itself. In this way, your fork acts as a bridge between the original repository and your copy where you can contribute back to the original project using a ```pull request```.

###### When should I fork or clone a repo?

(From toolsqa.com) Changes made to the forked repository can be merged with the original repository via a ```pull request```. A pull request alerts the repository owner and says "I have made some changes, please merge these changes to your repository if you like it". 

On the other hand, changes made to a cloned repository on the local machine can be pushed to the upstream repository directly. For this, the user must have the write access to the repository otherwise this is not possible. If the user does not have write access, the only way to go is through the forked request. So in that case, the changes made in the cloned repository are first pushed to the forked repository and then a pull request is created. 

It is a better option to ```fork``` before ```clone``` if the user is not declared as a contributor.

<a name="pr"></a>
##### Git pull request workflow

1. Fork the repo to your git account (only needs to be done once)
2. ```Fetch Upstream``` to merge any changes in the original repo with your fork.
3. Create a new branch to hold your changes
4. Clone your repo to your computer.
	Note: Clone only when you have write access (i.e. your repo). Use a ```pull request``` to send suggested changes to repo you have no write access for.
	```bash
	$git clone YOURUSERNAME/YOURFORKEDREPO
	```
5. 'Checkout' the new branch for editing
	```bash
	$cd YOURCLONEDREPO
	$git checkout YOURNEWBRANCH
	```
6. Make changes to the clone on your computer.
7. add, commit and push your changes to your repo.
	```bash
	$git add .
	$git commit -m "a commit message here"
	$git push origin YOURBRANCHNAME
	```
8. Check your forked repo is up to date with the original (```Fetch Upstream```) - resolve any merge conflicts.
9. Open pull request to merge YOURFORKEDREPO/YOURNEWBRANCH into YOURFORKEDREPO/MASTER (Check this is the case)
10. Merge.
11. Open pull request to merge YOURFORKEDREPO/MASTER into ORIGINALREPO/DEV (Check this is the case)
12. Pull request will then be received by the ORIGINALREPO and then considered to be added.
13. You can now delete YOURNEWBRANCH.