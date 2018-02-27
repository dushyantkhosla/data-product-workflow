# The Case against Notebooks

The main cause of unmaintainable code and bad code structure in Data Science is the mixing of exploratory "throw away" code with production code, and the use of ad-hoc interactive & presentational environments. Notebooks, are being used to write code that is ultimately deployed in production. This is not what notebooks where invented for, they are essentially browser based shells & presentation tools with charts and code blocks. Notebooks do not have refactoring tools, code structuring tools and are notorious for version control management.

In web-development the back-end development is done using different tools to the front-end development. In Data Science we need a separation too - different directories and toolsets for Exploration and Production.



# Motivation

> “I’ve found that refactoring helps me write fast software. It slows the software in the short term while I’m refactoring, but it makes the software easier to tune during optimization. I end up well ahead.”

- Organize **code** so subsequent exploration becomes faster
- Reorganize **text** (markdown) and images (plots) from notebooks into Reports that are easier to read.

# Goal

- Reduce the code-to-text ratio
  - Notebooks should be light on code, heavy on narrative
  - Can serve as Reports to a Technical audience
- Separate useful code that produces valuable insight from the failed experiements

# Method

If you’re going to do something

- **Once**
  - Just write some code and document it very well.
  - You (or someone else) should be able to reproduce it later on.
- **Twice**
  - Write a *Function*.
  - *Docstring* detailing
    - *Functionality*: in simple **English**
    - *Parameters, Returns*: specify names and data types
    - *Examples*: optional
- **Thrice or more**,
  - Write a *Module* containing functions that become widely used in the analysis
  - Reduces the amount of code written in subsequent notebooks, accelerates development, and improves readability
    - the codebase becomes smaller, and easier to reuse and fix.
  - Functions that become particularly important, can be made more solid by writing unit tests

# Example

- https://github.com/scikit-learn/scikit-learn

# Packaging 101

- A Python _module_ is folder containing
  - an `__init__.py` file, and
  - a bunch of `.py` files that contain definitions/statements for classes, functions, and global variables.
- A Python _package_ is simply an installable group of Python modules.
  - Packages structure the Python namespace by allowing you to use _dotted module names_
  - For example, after importing `sklearn`, you access the `RandomForestClassifier` class in sklearn’s `ensemble` module by `sklearn.ensemble.RandomForestClassifier`
  - Packages can be downloaded and installed through `conda` and `pip` or from local files.

# 5 steps to create a package

- Create a folder with the same name as your repo to contain your package’s modules.
  - Example: Scikit-learn has a “sklearn” folder in their repo.

- Put an `__init__.py` file inside the root directory.
  - Any variables or functions created in this file will be available in the package’s namespace.
  - Example: Scikit-learn’s `__init__.py` file defines a `__version__` variable that can be accessed by `sklearn.__version__`

- Create folders in the root directory with `__init__.py` files of their own.
  - These will become _submodules_, and objects declared within `.py` files within these will be accessed via the _dot notation_

- Put a folder called `tests/` inside the root folder (and each submodule)
  - This will contain unit tests.
  - This folder should also have an `__init__.py` file, which can also be blank.
  - For each file `filename.py` in the root folder of your package/submodule, create a file `test_filename.py` in this `tests/` folder containing functions that assert the behavior of the code in `filename.py`.

- To make your package _installable_, place a `setup.py` file in the root directory.
  - To install your package on a new system
    - Clone the repo,
    - Navigate to the root directory of your project on the command line
    - Run `python setup.py install`
    - Now Python will be able to import your package by name on your computer.
  - Deploy your package to PyPI and then install it via pip
    - Configure the `travis.yml` file with your PyPI username and password

# Running Tests on a Package

- _Manually_: At the command line, run `nosetests path_to_project_folder`
- _Automatically_:
  - Use `Travis` for continuous integration
  - Put a `travis.yml` file in the root directory of your repository.
  - Go to Travis’s website and link your repository.
  - Done! The `travis.yml` file will cause Travis to automatically run `nosetests` on your code anytime your repository is updated.
