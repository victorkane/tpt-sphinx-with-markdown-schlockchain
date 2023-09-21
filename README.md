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

- commit

```bash
commit 7c3eddf2cc35fecc97a26c54e60d2c0cd9f9bd23 (HEAD -> master)
Author: Victor Kane <victorkane@gmail.com>
Date:   Thu Sep 21 17:16:38 2023 -0300

    Ch02 Scaffolding a Sphinx Site

 .gitignore |  4 +++-
 Makefile   | 20 ++++++++++++++++++++
 README.md  | 66 ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++--
 conf.py    | 27 +++++++++++++++++++++++++++
 index.rst  | 20 ++++++++++++++++++++
 make.bat   | 35 +++++++++++++++++++++++++++++++++++
 6 files changed, 169 insertions(+), 3 deletions(-)
```

#### Live reload

- Install `livereload` package via requirements.txt
- Add in `run_livereload.py` to specify watch steps for livereload
- Run `run_liverelaod.py` (in VS Code right-click on file and select `Run Python File in Terminal`)
- Point browser at [localhost served web app](http://127.0.0.1:5500/)
- Modify `index.rst` to see `livereload` at work
- commit

```bash
commit 7f94bb47d80772c0e750b1d073a3421815659274 (HEAD -> master)
Author: Victor Kane <victorkane@gmail.com>
Date:   Thu Sep 21 17:38:08 2023 -0300

    Ch02 install and use livereload

 README.md         | 28 +++++++++++++++++++++++++++-
 index.rst         |  2 ++
 requirements.txt  |  3 ++-
 run_livereload.py | 10 ++++++++++
 4 files changed, 41 insertions(+), 2 deletions(-)
```

#### Add Markdown

- Sphinx uses RST (re-structured text) but we want markdown
- We can add Markdown to Sphinx via [Myst](https://myst-parser.readthedocs.io/en/latest/)

> MyST - Markedly Structured Text - Parser
>
> A Sphinx and Docutils extension to parse MyST, a rich and extensible flavour of Markdown for authoring technical and scientific documentation.

- Install `myst-parser` package via `requirements.txt`
- To actually use markdown now with Sphinx, we need to tell Sphinx it's there by listing it as an extension in the `conf.py` file

#### First Markdown Page

- create `about_us.md`
- invoke from `toc` in `index.rst`

```bash
commit 880c6d4e1fbb3e46a535248e5c3c8d7105eb549f (HEAD -> master)
Author: Victor Kane <victorkane@gmail.com>
Date:   Thu Sep 21 18:29:51 2023 -0300

    Ch02 First Markdown Page

 .vscode/settings.json |  6 +++++-
 README.md             | 34 +++++++++++++++++++++++++++++++++-
 about_us.md           |  3 +++
 conf.py               | 19 ++++++++++---------
 index.rst             |  2 +-
 requirements.txt      |  3 ++-
 6 files changed, 54 insertions(+), 13 deletions(-)
```

#### Cleanup

- Cleanup in config file, etc.
- Convert index page to 100% markdown

```bash
commit 08037c452a420dcbafd6a49ff0779b77a4372891 (HEAD -> master)
Author: Victor Kane <victorkane@gmail.com>
Date:   Thu Sep 21 18:58:15 2023 -0300

    fix: remove indentation from toctree syntax for markdown

 index.md | 10 +++++-----
 1 file changed, 5 insertions(+), 5 deletions(-)

commit 5fefb80418bf2448170aff0ef3288a2feb723f3c
Author: Victor Kane <victorkane@gmail.com>
Date:   Thu Sep 21 18:55:29 2023 -0300

    Cleanup config file, etc; convert simple index page to pure markdown

 README.md | 23 ++++++++++++++++++++++-
 conf.py   | 18 ------------------
 index.md  | 10 ++++++++++
 index.rst | 22 ----------------------
 4 files changed, 32 insertions(+), 41 deletions(-)
```

### Chapter 03 Simple Markdown

#### Formatting

- We explore markdown formatting in the `about_us.md` file/page

#### Images

- We add an image in two ways (local static file and external)