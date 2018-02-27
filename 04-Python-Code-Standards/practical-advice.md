# Principles for Writing Good Code

> Good code shouldn’t just work. Good code should be easily understood by others who will need to work with it–including your future self. Given that, writing stylish code isn’t just fashionable; it serves an important purpose, helping others easily build upon your work.

- **Variables**
  - Avoid putting numbers that do not have a clear meaning, in your code.
  - Create a variable with an informative name to hold such numbers.

- **Naming Things**
  - Classes are always named in CamelCase.
  - **Functions** are always named in lower_case_with_underscores.
    - Begin the name of a function with a verb. Common choices: compute, get/set, find, is/has/can, add/remove, first/last.
    - This has the nice benefit of suggesting what the function will return

- **Docstrings** should contain
  - A single-sentence summary of the function
  - A paragraph or two that elaborates on that summary (if necessary).
  - A description of each of the function’s parameters
  - A description of each object that the function returns.
  - When in doubt, look at scikit-learn (or your favorite well-maintained open source project) for examples of great docstrings.

- **Imports**
  - One per line
  - Organize your imports into three sections (separated by newline):
    - first, packages in the standard Python library;
    - second, third-party packages;
    - third, application-specific packages.

    Example:

    ```python
    import os
    import sys

    import pandas as pd
    import seaborn as sns

    from src import get_data
    ```

- **Style**
  - USe packages like `pep8`, `pyflakes` or `pylint` to test your code for compliance with Python’s PEP8 style guide. 
