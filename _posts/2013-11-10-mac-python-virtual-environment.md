---
layout: mac

title: Python Virtual Environment

description: Setting up an RVM ish environment in Python

excerpt: 

author: Ted Hagos

lastupdate: 2013-11-10


tags:
- python
- virtual
- environment
- OSX
- Mac

---


<pre class="codeblock">
$ brew install python
</pre>

Yes, I know OSX comes with Python pre-installed, but this formula for python comes with pip and setuptools. 

Just to make sure pip and setuptools are up to date, do this also

<pre class="codeblock">
$ sudo pip install --upgrade setuptools
</pre>

## Virtual Environment Setup

<pre class="codeblock">
$ sudo pip install virtualenv
$ sudo pip install virtualenvwrapper
$ mkdir ~/pythonenvs
$ echo "WORKON_HOME=~/pythonenvs" >> ~/.bash_profile
$ source /usr/local/virtualenvwrapper.sh   
</pre>

Quit and re-open the terminal for the changes to take effect &mdash; or just launch another terminal window and work there.

## Usage 

<pre class="codeblock">
$ mkvirtualenv gae
$ mkvirtualenv standard
$ workon gae
$ workon standard
</pre>

## Another Usage

1. mkdir ~/workarea/notes-gae (if you are working on a Python Google App Engine project, for example)
2. cd to it
3. mkvirtualenv notes-gae
4. work on notes-gae, install some new eggs, site packages
5. write the software to install inside requirements.txt, Ian Bicking wrote something about this
6. then pip -r requirements.txt
7. you can use yolk -l to see what packages are installed in the env
8. then use pip freeze > stable-requirements.txtto freeze the software versions
9. Use deactivate command to get out of virtual environments
10. version the project, git init (gotta use git for source control)
11. add some files to the project, then git add .
12. do some commits, git commit -m “comments”
13. and push the commits to a remote repo, git push -u origin master
14. When you pick the project up another day, remember to git pull, before doing anything else

## Why do it

A virtual environment setup keeps python packages across projects separate. They have independence. That's a good thing. When you are working on a new python project, you can't avoid installing python packages for it. If the new packages does not agree with packages you have installed for other projects, you are in for a bag of hurt. If the packages were managed using virtual environments, the independence of packages start becoming valuable.


