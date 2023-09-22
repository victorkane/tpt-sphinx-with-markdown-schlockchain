## Schlockchain

### Setup (after cloning this repo)

- clone repo
- open repo directory with `code .` for VS Code
- In a terminal do the following

```bash
$ python3 -m venv .venv
$ source .venv/bin/activate
$ pip install --upgrade pip
$ pip install -r requirements.txt
$ make html
$ python run_livereload.py
```

- Point your browser at `http://127.0.0.1:5500/` to see site running with livereload

### Chapter 02 Setup (for following the tutorial and creating everything from scratch)

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

#### Sphinx Themes

- [Builtin Sphinx theme options and third-party themeso](https://www.sphinx-doc.org/en/master/tutorial/more-sphinx-customization.html#using-a-third-party-html-theme)
  - [Builtin Sphinx Theme directory](https://www.sphinx-doc.org/en/master/usage/theming.html#builtin-themes)
  - [Third-party Sphinx Themes Gallery](https://sphinx-themes.org/)
    - [Book Theme](https://sphinx-themes.org/sample-sites/sphinx-book-theme/)
      - dark/light switc, double toc, beautiful like Astros special doc thingie
    - [Furo](https://sphinx-themes.org/sample-sites/furo/) es furor (built for Python docs)!
      - dark/light switc, double toc, beautiful like Astros special doc thingie
      - smooth scrolling!
    - [Nefertiti Theme (two Toc, smooth scrolling)](https://sphinx-themes.org/sample-sites/sphinx-nefertiti/#quickstart)

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

#### Markdown and Sphinx

- Sphinx is a SSG, but not just another one
- Incredible features: [Sphinx docs](https://www.sphinx-doc.org/en/master/)

### Chapter 04 More Authoring

#### Images

```bash
commit ab8e5964e7aaaf5877b02a6d9e36b7e2be6c3ba4 (HEAD -> main, origin/main)
Author: Victor Kane <victorkane@gmail.com>
Date:   Fri Sep 22 04:48:18 2023 -0300

    Ch04 More authoring images with Myst code fences, references with roles

 README.md   |  7 ++++++-
 about_us.md | 15 +++++++++++++++
 conf.py     |  3 +++
 index.md    |  2 ++
 4 files changed, 26 insertions(+), 1 deletion(-)
```

#### TOC: Table of Contents

```bash
commit c8a252e9ddff96dbe973e528640b43ba818ca859 (HEAD -> main, origin/main)
Author: Victor Kane <victorkane@gmail.com>
Date:   Fri Sep 22 05:28:30 2023 -0300

    Ch04 TOC: Table of Contents in both rst and yaml syntax

 README.md | 13 +++++++++++++
 index.md  | 15 +++++++++++++++
 2 files changed, 28 insertions(+)
```

#### Directives and Downloads

- See [Sphinx docs: directives](https://www.sphinx-doc.org/en/master/usage/restructuredtext/basics.html#directives)
- Download an image as a static file

```bash
commit 5ec853e50fbc3ea8b6422a15c5d569aa77872285 (HEAD -> main)
Author: Victor Kane <victorkane@gmail.com>
Date:   Fri Sep 22 05:46:30 2023 -0300

    Ch04 Directives and Downloads

 README.md   | 21 ++++++++++++++++++++-
 about_us.md | 27 +++++++++++++++++++++++++++
 2 files changed, 47 insertions(+), 1 deletion(-)
```

#### Serverless Search

- Built in via reverse index javascript library included in static sites
- Slow for very large sites, so for example `read the docs` sites use server side `Elastic Search` instead for better performance.

### Chapter 05 Linking

#### How Sphinx Linking Works

> Sphinx... keeps kind of a database of all the documents in your sight and everything that is linkable targets and it keeps the path and the title of all of the documents and resources. So that when you make a link, it can insert the title and update the title in the link text.
>
> If you change the targets title, it's not just for documents in this example we did colon dot colon. But if you did colon ref colon, you could point to a location that was a role; [a] target somewhere in a document for example, a section heading.
>
> And then one other thing that Sphinx can do in addition to providing you the link text and deep linking into a document is it will warn you if you link to something that doesn't exist and that's really not something you can get from some of these other static site generators.

#### Markdown linking

- Links to Sphinx linking via Myst Parser
- Empty Link Text for markdown links automatically grabs title of target (dynamic, so if it changes in the future, you're covered! "not something you get from other static site generators!)

#### Headings and roles

- Sphinx uses the term `roles` for linkable markers (like headings) on a page
- If you designate a heading as a role:

```markdown
(investors)=

## Investors
```

- and then on, say, the index page `ref` that role:

```markdown
You can also visit our {ref}`investors`.
```

- then Sphinx searches for that role, warns if it cannot find it, and when it does, extract the title as the link text, and link to that section in the page and section being referenced (we reference `Investors` in about_us from index (see commit below))
