# GIX Git Demo
Demo repository for TECHIN514


This lab is designed to become familar with github and conda.  

Github is the tool for sharing code and working on projects together.  Its also sometimes important to manage dependencies so that everyone is running from the same set of libraries.

We can do this with package managers or with  virtual environments. conda is a popular package manager that makes it easy to manage a list of library dependencies that might need to be installed, and its popular for data science applications, and not language specific.  poetry is another one which is increasing popularity, but specific to python. 

<p align="center">
  <img src="https://github.com/manidarla/GIXdemo/blob/main/git-tower.png" alt="git-tower image"/>
</p>

Image from git-tower.com/learn/git/ebook/en/command-line/remote-repositories

So for this lab... 

Install github and miniconda

(Install git on Windows
https://git-scm.com/download/win

Install git on Mac and Linux
https://git-scm.com/book/en/v2/Getting-Started-Installing-Git

Install miniconda/anaconda
https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html)


Follow the instructions provided in the lecture presentation. While testing, If entering your password during git push doesn't work check the below link for PAT:

https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token

You will be able to perform basic git operations with this information.

&nbsp; 

## Activating existing environment:

Now clone this repository (GIXDemo) onto your computer.

it includes a conda environment yaml that you'll need to activate.

from the respository, create a new conda environment from GIX514Demo.yaml

`conda env create --file GIX514Demo.yaml`

and activate the new environment using

`conda activate GIX514Demo`

(The yaml file contains libraries supported by osx-arm64. It may not create the environment desired in all systems. So, you can capture the base python and numpy versions of your system)


and run the python script `GIX_envtest.py`

You should see the version numbers for python and the installed numpy package. Record these for your answer.... 

&nbsp; 
&nbsp; 
&nbsp; 


## Creating new environment:
Now let's do the same for someone else and setup an environment to share! (Also can be done in same system but in a different directory)

create a new public repository, name it TECHIN514-xxxxx where xxxxx is whatever you think is a good name copy the file env-test.py from this repo into your new repository. (You can test commit and push your local repo to a remote repo here)

As a task, You'll also need numpy installed, and we'll specify a specific version, and to do that we'll use conda.

Let's say for exmaple we need a specific version of numpy to be compatible with our code e.g. 1.19.2 (even though the current version might be 1.21)

create a new conda environment called GIX514Assignment that includes numpy 1.19.2

`conda create --name GIX514Assignment python=3.8 numpy=1.19.2`

To test this, first make sure you are in the conda base environment or not in conda at all.  if you're not there already, you can get there with

`conda activate base` (to get to your base environment)
or
`conda deactivate` (to get out of conda environment entirely.  you may have to do this multiple times)


start python and note the current version.  and the version of the numpy library.  On my computer for example... 

```
Python 2.7.18 (default, Nov 13 2021, 06:17:34)
[GCC Apple LLVM 13.0.0 (clang-1300.0.29.10) [+internal-os, ptrauth-isa=deployme on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import numpy as np
>>> print(np.__version)
1.8.0rc1
>>>
```

Then check the list of available conda environments 

`conda env list`

you should activate environment you just created, `GIX514Assignment`.  you can activate it with

`conda activate GIX514Assignment`

you'll see the prompt change to show the active environment.  now repeat the same steps and note your python and numpy version.

```
(GIX514Assignment) blah@blahblah ~ % python
Python 3.8.11 (default, Aug 16 2021, 12:04:33)
[Clang 12.0.0 ] :: Anaconda, Inc. on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import numpy as np
>>> print (np.__version__)
1.19.2
```

Pretty cool!  we've specified our environment exactly.
Now export your environemnt so you can share it with someone else.

`conda env export --name GIX514Assignment > GIX514Assignment.yaml`

## Fork, pull request and merge:
Github is a powerful tool when a project is developed and maitained by mutiple contributors. It allows contributors to freely edit and test after forking the repo to their own, and create a pull request to contribute to the original project. And the maintainer of the original project can review that request and decide whether to merge the new changes.

First, a team meber other than the owner of your team repo should fork the repo (your team's repo, not this repo) to his/her/their own. Please refer to: https://docs.github.com/en/get-started/quickstart/fork-a-repo

Next, in the new forked repo, add one more line to to 'GIX_envtest.py'

`print('This is Team []')`

Then, create a pull request, please refer to: https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request-from-a-fork

Finally, the owner of your team repo can review and merge the pull request, please refer to: https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/incorporating-changes-from-a-pull-request/merging-a-pull-request

### Resources and Notes:
This is a good cheat sheet for conda https://docs.conda.io/projects/conda/en/latest/_downloads/843d9e0198f2a193a3484886fa28163c/conda-cheatsheet.pdf

If you meet errors like:

`- 'git' is not recognized as an internal or external command, operable program or batch file.`
Please refer to the following page and change your Windows PATH variable.
https://stackoverflow.com/questions/4492979/git-is-not-recognized-as-an-internal-or-external-command

`- zsh: command not found: conda`
(For Mac users), refer:
https://stackoverflow.com/questions/44597662/conda-command-is-not-recognized-on-windows-10

After you install conda, it will try to activate every time you open a shell/terminal window.  To prevent conda on your system in activating by default, use the following:

`conda config --set auto_activate_base false`

