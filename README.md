# OpenDeathValley


[![Documentation Status](https://readthedocs.org/projects/opendeathvalley/badge/?version=latest)](http://opendeathvalley.readthedocs.io/en/latest/?badge=latest) [http://opendeathvalley.readthedocs.io][odv_readthedocs]

## Documentation

Documentation is written in Sphinx, you will need python and sphinx installed to build it.

### Requirements


* [Python][python]
* [Sphinx][python_sphinx]
* [Read the Docs Sphinx Theme][sphinx_rtd_theme]

### Style guide

    H1 => ========
    H2 => --------
    H3 => ^^^^^^^^
    H4 => """"""""
    H5 => ''''''''
    H6 => ********

### Usage

    > make.bat html
    > cd build\html
    > python -m http.server 8080

Documentation can be browsed at `http://127.0.0.1:8080/`

[python]: http://www.python.org/getit/
[python_sphinx]: http://www.sphinx-doc.org/en/stable/
[sphinx_rtd_theme]: https://github.com/readthedocs/sphinx_rtd_theme
[odv_readthedocs]: http://opendeathvalley.readthedocs.io