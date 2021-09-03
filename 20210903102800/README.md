# Working with virtual Environments correctly.

Python has many different virtual environment packagers including venv,
virtualenv, conda and pipenv. All of which do very similar things. Venv
is shipped with python from 3.3 onwards so is available at all times.
The disadvantage to venv is that it is python version specific, ie you
are only able to make virtual environments for python3.8 in the 3.8
version.

This zet outlines how to use virtualenv on your system

There are numerous ways to setup a virtual environment configuration. We
can download from pip and install globally or user space. If we want to
remove it from any system conflicts we can use a bootstraper from
[bootstrap](https://bootstrap.pypa.io/virtualenv.pyz). This can be
called with
```bash
curl -O https://bootstrap.pypa.io/virtualenv.pyz
```

We can then initialise the virtualenvs with:
```bash
python3 virtualenv.pyz <envname>
```
However it is important to note that the virtual environment gets
created in whichever directory you are working in. It is possible to
create a single directory and create all venvs in that directory. To do
this we can create a bash script to run venv setup, venv list and venv
activate. These commands create a virtual environment in a dedicated directory such
as a repos directory. list will show all venvs available. When you run venv
activate it will source the particular environment. The script can be
seen in my scripts folder in my dotfiles.



