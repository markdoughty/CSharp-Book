# Git 101

> "What is this Git thing all about ..?"
>
>> *Awareness is the greatest agent for change* <sub>Eckhart Tolle</sub>

## Git?
[Git](https://git-scm.com) is a version control system (VCS), which allows you to keep track of changes in files. It also coordinates the files and their changes among multiple people - a project team for example - or simply for yourself. Have a look at the [Pro Git](https://git-scm.com/book/en/v2) (Chacon and Straub, 2014) book to lift the lid on Git features.

Git is [widely used](https://en.wikipedia.org/wiki/Git) in industry as a VCS, and as such can be an essential skill to learn as part of your University studies. Many [existing](https://git-scm.com/book/en/v2/Appendix-A%3A-Git-in-Other-Environments-Graphical-Interfaces) coding tools have built-in Git extensions - including Visual Studio. These allow you to easily link your code project, Git and your chosen IDE.

Within Git, the files for each project that you create are collected together in a repository, or 'repo'. On your local computer, the project will contain a ```.git/``` folder containing all the information related to the files in the project, any changes over time, etc. If you delete this folder, your project is no longer considered a Git repo on your local computer.

The basic structure comprises of a 'local repository' which is on your computer, and this is linked to a 'remote repository' on Github. There are, in fact, four distinct that your files need to pass though:
1. The 'Working Folder'
2. The 'Staging Area'
3. The 'Local Repository'
4. The 'Remote Repository'

Everything you may do with Git involving moving files from your computer to a remote repository, and 'cloning' or downloading them from the remote to your computer, will involve moving between these four areas. 

## Getting Started
If you haven't already, download and install Git for your OS from [here](https://git-scm.com/download/). Accept all default options. 'Git bash' should now be a context menu (right click in Windows) option.

You can create a repo and interact with Git in a number of ways - through an IDE such as Visual Studio, or manually.

#### Git in Visual Studio

Look [here](https://devblogs.microsoft.com/visualstudio/improved-git-experience-in-visual-studio-2019/) and [here](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Git-Fundamentals) for information on the latest Git for Visual Studio developments (as of April 2020) and more tutorials. 

*To 'clone' or download a remote repository and open it in Visual Studio:*

```File > Clone or Checkout Code```

In the Github repo, see the green ```Clone or download``` button? Press this button, and the URL you see is the repository location. Copy and paste this into the ```Repository location``` field in Visual Studio.

*To add an existing project in Visual Studio to a version control system, such as Git:* 

With the project open, in the IDE, click ```Add to Source Control``` in the bottom right of the window, and then paste in your remote Git repository address. Click ```Publish``` and then you should see your project as a repo on Github.

 #### Git using Git bash

 Have a look at [this](https://www.atlassian.com/git/tutorials/git-bash) for more information on Git bash.

 If you haven't already, create an account at [github.com](https://github.com)



