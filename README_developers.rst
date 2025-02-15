.. _developersnotes_contrib:

Contributing
=============

If you find bugs, errors, omissions or other things that need improvement,
please create an issue or a pull request at
https://github.com/vincenzooo/pyXsurf.
Contributions are always welcome!

Here is summarised the current status and the best practices for development for code, documentation, packaging, and testing.
This is a work in progress, the project is going through a major restyling with the intent of standardizing the workflow for updates of software and documentation, but many aspects are still being defined.

If you are interested in contributing, please check often these pages. In the meanwhile you are very welcome to signal any problem or missing information, especially if anything is not working as documented or if you can point to templates or examples.

.. _developersnotes_install:

Developers Installation
------------------------

To start, it is suggested to clone the latest
development version (a.k.a. "master") with Git::

   git clone https://github.com/vincenzooo/pyXsurf.git

then move to the project folder and install as developer::
    
   cd pyXsurf
   pip install -e .

where ``-e`` stands for ``--editable`` (don't forget the final ``.`` for the current directory).
This method installs the library directly from the current location, which differs from a standard installation. In a regular installation (without the -e option), Python compiles and links to a copy of the code, typically located in the site-packages folder. However, with an "editable" installation, the code isn't copied; instead, it's linked directly from the source folder. This means any modifications made to the code in the source folder are immediately reflected in the imported library, maintaining the import synchronized with the software (in other words, you don't need to reinstall the package every time you make changes). This will work also if you checkout another branch (you might need to reimport the module in that case).

In addition, if you are using IPython or derived tools (e.g. Jupyter notebooks) it is suggested to add the following magic commands at the beginning of your work:

   %load_ext autoreload
   %autoreload 2

This will automatically make sure that the code is reimported at any change.

Working on documentation
-------------------------

If you want to work on the documentation only, you can modify the documentation source in ``docs\source`` folder. To compile documentation locally, you can call, from the ``docs`` directory:

+ ``make html`` will normally compile the "official" documentation for the pyXsurf library at the current status of development.
+ ``make html .\source_test_doc`` will compile also the test documentation, creating a front page which links to the "official" documentation, but also at a test documentation, where the dubious concepts are tested in details.

In both cases the compiled HTML documentation will be visible in ``docs\build\html\index.html``.

You can refer to the official pages of ``Sphinx`` and ``nbspinx`` tools for reference and syntax guide:

.. _PSphinx: https://www.sphinx-doc.org/en/master/tutorial/getting-started.html
.. _nbsphinx: https://nbsphinx.readthedocs.io/


If you modify any file, and you suspect it could be an improvement, please write to vincenzo.cotroneo@inaf.it, or use regular git functions (``pull requests`` or ``issue tracker``, you probably know this stuff better than I do).

.. note::
    Themes are defined in the ``conf.py`` file of each folder, so there might be a difference in the aspect of the "official" documentation, according to which compilation command is run. TODO: make this point uniform, by making the configuration for tests to recall the configuration for the "official page".


Active Branches
-------------------------------------------------

At the moment, the updated project is on the master branch, which is the only used. In the past there were attempts to establish development branches, which are now not maintained and are:

* **documentation** The most recent branching, it is mostly devoted at developing better sphinx documentation
* **readers_dev** Development to Reader routines for I/O of file formats 


Roadmap
=======

The roadmap is detailed in the following section, main area of work are:

*  documentation
*  testing
*  installation
*  continuous Integration

Status of installer
-------------------------------------------------

The library is installable with common python practices, downloading code from github repository.

I have tried the installation on a few computers and it worked smoothly 
by ``setup.py``. The folder ``test_install`` contains tests 
that verify a correct installation.

Last time I tried, I could upload the package on test-PyPI, but not on the main PyPI, as I get an error, related to the too large size of the package. 

A complete CI/CD mechanism needs to be implemented. Plan is to achieve a full installable distribution on PyPI, and possibly on conda, and be able to maintain it through Continuous Integration.

Code and comments to code
-------------------------------------------------

Code is quite consistent, and usually commented, but there are still a few modules in early stage of development or which might be removed or integrated somewhere else. Some are included for backwards compatibility, future needs or just to stay on the safe side of breaking dependencies. 
There might be additional features which I lost along the way while experimenting with git and might decide to reintegrate if I recover them for other needs.

Status of docs
-------------------------------------------------

Docstrings are scattered around the code and sometimes even in the right place for self-documentation to work, 
but this is quite non-uniform,
as it mixes different conventions I tried over the time, and it will remain like this
until I find one tool that I can use to maintain the documentation.

TODO: build a minimal set of commented modules and functions with a decently clean API documentation API automatic documentation, as a starting point for a refinement of the standard in documentation format, which is often not homogeneous.  

There were past attempts of ``documentation`` branch or similar, they are now merged in the main branch. In `\docs\source\test_source_docs` contains some tests for documentation rendering and working to test syntax and features "offline". It can be compiled with ``make file\source_test_docs``.

Jupyter notebooks are implemented in different ways according to the original position (which is most of the times arbitrary and not standardized):

* `notebooks`: here are "well-behaving" jupyter notebooks. These work and can be referred from rst files and are compiled by means of jupyter extensions. Each of these generate a `.html` file in `\docs\build\html\notebooks` 
* Some notebooks are originally located in directories above `docs\source` or in their subfolders (e.g.: `\source\pySurf\test`). These seems to be not accessible for compilation from `sphinx`. As a workaround, those were copied to `\docs\source\_static` and need to be manually compiled to html with `nbconvert`

TODO: find a definitive solution for notebooks above sphinx root.
TODO: understand different examples of link to notebook by embedding or linking from ipynb or rst pages. 

Status of tests
-------------------------------------------------

There are no standardized tests. Each package has its tests in form of .ipynb or .py files and more in the source code.

TODO: implement organized test structure (e.g.: pytest).

Changes
-------------------------------------------------
2023/12/04 Updated status of the project and TODO on this file.
2023/07/15 Starting implementing major changes towards common standards and best-practices. 
2022/09/06 Created new branch ``pyXsurf_nbdev`` for experimenting with
2021/07/21 Upgraded installation mechanism.
2020/11/09 Changed repository name from ``pyXTel`` to
``pyXSurf``.

2022/03/31 started documentation branch. Upgrades to sphinx docs and github readme and readme_developers. did more attempts in separate folder based on astropy and astropy templates. See VS workspace.

2022/03/22 Started restructuring repository. Renamed "source" folder to source (from pyXsurf). Add installation instructions for developers to this file and readme.txt.

2021/07/21 Upgraded installation mechanism.

2020/11/09 Changed repository name from ``pyXTel`` to
``pyXSurf``.

2021/07/21 Really trying to improve installation and release.
Mostly following https://medium.com/free-code-camp/from-a-python-project-to-an-open-source-package-an-a-to-z-guide-c34cb7139a22 and based on astropy template.

References
------------
The library was developed on anaconda
distribution. Any other distribution should be equivalent, however I
suggest the use of a package manager, found Anaconda quite easy to work with,
so I can only recommend it. Same way, I used for developement
VSCode (when memory allowed) or notepad++/IPython/jupyter on Windows; I feel to
recommend any of these to new users and wiling contributors. Of course any other environment or editor works same way.

if you are not sure of what you are doing (as I am most of the time), feel free to keep it locally and use only ``git`` or to use any expertise you have (and I don't necessarily do have).

This is a good page explaining the basic usage of ``git`` 
https://kbroman.org/github_tutorial/pages/routine.html


See https://stackoverflow.com/questions/19048732/python-setup-py-develop-vs-install for comments on installation modes.

TODO: summarize here.
