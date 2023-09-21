## Schlockchain

### Chapter 02 Setup

#### Create Project

If using VS Code, first make sure the Python extension is installed

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
```

#### Install Sphinx

```bash
(.venv) victorkane@Victors-MacBook-Air schlockchain % cat requirements.txt            
sphinx%  
(.venv) victorkane@Victors-MacBook-Air schlockchain % which pip
/Users/victorkane/Work/Learn/python/static-sites-sphinx-markdown/schlockchain/.venv/bin/pip
(.venv) victorkane@Victors-MacBook-Air schlockchain % pip install -r requirements.txt 
```

- check if Sphinx is installed

```bash
(.venv) victorkane@Victors-MacBook-Air schlockchain % which sphinx-quickstart
/Users/victorkane/Work/Learn/python/static-sites-sphinx-markdown/schlockchain/.venv/bin/sphinx-quickstart
```

- Commit

```bash
(.venv) victorkane@Victors-MacBook-Air schlockchain % git log --stat
commit 0ddf32121bd49694450d0ff667d707c0c360e582 (HEAD -> master)
Author: Victor Kane <victorkane@gmail.com>
Date:   Thu Sep 21 16:47:38 2023 -0300

    initial commit: Sphinx installed in Python virtual environment

 .gitignore            |  1 +
 .vscode/settings.json |  3 +++
 README.md             | 28 ++++++++++++++++++++++++++++
 requirements.txt      |  1 +
 4 files changed, 33 insertions(+)
(.venv) victorkane@Victors-MacBook-Air schlockchain % 
```

#### Make a Sphinx site

```bash
(.venv) victorkane@Victors-MacBook-Air schlockchain % sphinx-quickstart
Welcome to the Sphinx 7.2.6 quickstart utility.

Please enter values for the following settings (just press Enter to
accept a default value, if one is given in brackets).

Selected root path: .

You have two options for placing the build directory for Sphinx output.
Either, you use a directory "_build" within the root path, or you separate
"source" and "build" directories within the root path.
> Separate source and build directories (y/n) [n]: 

The project name will occur in several places in the built documentation.
> Project name: Schlockchain
> Author name(s): Victor Kane
> Project release []: 

If the documents are to be written in a language other than English,
you can select a language here by its language code. Sphinx will then
translate text that it generates into that language.

For a list of supported codes, see
https://www.sphinx-doc.org/en/master/usage/configuration.html#confval-language.
> Project language [en]: 

Creating file /Users/victorkane/Work/Learn/python/static-sites-sphinx-markdown/schlockchain/conf.py.
Creating file /Users/victorkane/Work/Learn/python/static-sites-sphinx-markdown/schlockchain/index.rst.
Creating file /Users/victorkane/Work/Learn/python/static-sites-sphinx-markdown/schlockchain/Makefile.
Creating file /Users/victorkane/Work/Learn/python/static-sites-sphinx-markdown/schlockchain/make.bat.

Finished: An initial directory structure has been created.

You should now populate your master file /Users/victorkane/Work/Learn/python/static-sites-sphinx-markdown/schlockchain/index.rst and create other documentation
source files. Use the Makefile to build the docs, like so:
   make builder
where "builder" is one of the supported builders, e.g. html, latex or linkcheck.
```