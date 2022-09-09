pyXsurf (formerly pyXTel)
=========================

Python library for X-Ray Optics, Metrology Data Analysis and Telescopes
Design. 

2021/07/21 Upgraded installation mechanism.
2020/11/09 Changed repository name from ``pyXTel`` to
``pyXSurf``.

Installation
------------

Download or clone the project. You can use git clone command by:
``git clone https://github.com/vincenzooo/pyXSurf.git`` or the button
``download`` at top of page. It can be advisable to update your environment, and especially ``pip`` to the most recent version.
At this point you have two options:

1. Python installer (suggested): move to the folder with the code and call
``python setup.py install``. This will perform a "regular" installation (meaning that the 
code is copied to ``site-packages`` folders, which holds all installed Python libraries) and 
made accessible to your system.

2. Manual (developer): as in option 1, just use ``pip install -e .``.
Doing this, the library will be installed from current position (no local copy), any change to the original code will be immediately
available in the imported library.

At this point you can open Python and try ``import pySurf``, if this works without errors, you can go to the tutorials section.

Code can be uninstalled in same way with ``pip uninstall pyXsurf``, or calling directly the setup file ``python setup.py develop  -u`` (uninstalling developer installation is expected to work only with most recent pip versions, at least >=19.1.1)).

There are developer branches on github, which have extra functionalities at the moment under development (they are quite messy, so feel free to ask if you are looking for something in particular). These can be installed in the same way and should work equally (just have more unfinished stuff). For git beginners, the only thing you need to do differently, is to switch branch, e.g. ``git checkout documentation`` (where ``documentation`` is the name of the branch) before running the setup. Please check developers notes for a list of active branches and their features and for more details. Also, if you plan to make changes to the code and want to keep the changes automatically in synch, remember to install the code in "developer mode" (as explained above).

Status of the library
--------------------------------

The main part of the library is well defined and it works well. I am
constantly adding functions when I find they are needed during my daily
work. 

I have tried the installation on a few computers and it worked smoothly by `setup.py`. You are very welcome to help signaling any problem or missing information, please see :ref:`Contributing` below.

If everything worked well with the installation, there
are a decent number of tutorial and examples, but they are quite scattered around in
folders ``Demo``, ``Tutorial``, ``Test``, etc. 

You should be able to access information by usual python introspection (``?``, ``??``, autocompletion, etc.).

See developer notes :ref:`developersnotes` for a detailed status of developement, how to access more recent features and last status of documentation (on developer brach), especially if you think you can help.
Expecially installation and release mechanism, are in phase of improvement, as well as documentation.

.. _contributing

Contributing
--------------------------------

Please report bugs or feature requests, missing documentation, or open a issue on github https://github.com/vincenzooo/pyXsurf/issues.

Expecially appreciated is if you can provide templates, examples or hints on how to handle, documentation (Sphinx), packaging, continuous integration (Github).

Please check :ref:`README_developers` for the status of the development, or if are willing to help in any way. 


Modules
-------

A basic description of the different modules is: 

* **dataIO** Generic routines for accessing and manipulating data and files. 

* **notebooks**  Jupyter notebooks, not necessarily related to the libraries, include test and experiments on python. 

* **plotting** Plotting functions for pySurf data. 

* **pyGeo3D** Functions for geometry in space (lines and planes). 

* **pyProfile** Equivalent of pySurf acting on Profiles. 

* **pySurf** Functions and classes acting on 3D points or surfaces. 

* **thermal** Functions for modelling of thermal forming of glass.

Some examples and data can be found in a ``test`` subfolder of each
module.

Citation
--------

.. image:: https://zenodo.org/badge/165474659.svg
   :target: https://zenodo.org/badge/latestdoi/165474659

License
-------

This project is Copyright (c) Vincenzo Cotroneo and licensed under
the terms of the BSD 3-Clause license. Parts of this package are based upon
the `Astropy package template <https://github.com/astropy/package-template>`_
which is licensed under the BSD 3-clause license. See the licenses folder for
more information.


Author
------

Vincenzo Cotroneo vincenzo.cotroneo@inaf.it
