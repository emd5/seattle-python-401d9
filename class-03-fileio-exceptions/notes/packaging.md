# Creating Your Own Python Package

It’s important to note that the term “package” in this context is being used as a synonym for a distribution (i.e. a bundle of software to be installed), not to refer to the kind of package that you import in your Python source code (i.e. a container of modules). It is common in the Python community to refer to a distribution using the term “package”. Using the term “distribution” is often not preferred, because it can easily be confused with a Linux distribution, or another larger software distribution like Python itself.[1](https://packaging.python.org/tutorials/installing-packages/)


## The Python Package Index
The Python Package Index is a repository of software for the Python programming language. There are currently almost 130k packages listed under the service.

For additional information on Installation of packages, please refer back to the [PyPi Documentation](https://packaging.python.org/tutorials/installing-packages/#use-pip-for-installing) .

## Setup.py walk-through
For a project to be considered a "package" it must be bundled with the appropriate configuration of files and directories which will support the distribution of that project through the PyPi system. The most important file is the `setup.py` file. It's essentially a primary point of configuration and documentation (readable syntax for the PyPi system) for publishing and installing the package.

### `setup.py`
`setup.py` serves two primary functions:

It’s the file where various aspects of your project are configured. The primary feature of `setup.py` is that it contains a global `setup()` function. The keyword arguments to this function are how specific details of your project are defined. The most relevant arguments are explained in the section below.
It’s the command line interface for running various commands that relate to packaging tasks. To get a listing of available commands, `run python setup.py --help-commands`.

[Click here](https://github.com/pypa/sampleproject/blob/master/setup.py)  for a reference to a fully commented example of a `setup.py` document.

Below is a simple example of arguments which are configured in a project.

```python
from setuptools import setup, find_packages
from codecs import open

# Arguments marked as "Required" below must be included for upload to PyPI.

setup(
    name='sampleproject',  # Required
    version='1.2.0',  # Required
    description='A sample Python project',  # Required
    url='https://github.com/pypa/sampleproject',  # Optional
    author='The Python Packaging Authority',  # Optional
    author_email='pypa-dev@googlegroups.com',  # Optional
    keywords='sample setuptools development',  # Optional
    packages=find_packages(exclude=['contrib', 'docs', 'tests']),  # Required
    install_requires=['peppercorn'],  # Optional
)
```

For a full list of `setup.py` arguments refer to the [documentation](https://packaging.python.org/tutorials/distributing-packages/#setup-args) .

### `README.md` or `README.rst`
_Note: rst (reStructuredText) is a common markup language similar to Markdown, and commonly used in association with Python documentation._

All projects should contain a README file that covers the goal of the project. The most common format is reStructuredText with an “rst” extension, although this is not a requirement.

### `LICENSE.txt`
Every package should include a license file detailing the terms of distribution. In many jurisdictions, packages without an explicit license can not be legally used or distributed by anyone other than the copyright holder. If you’re unsure which license to choose, you can use resources such as GitHub’s Choose a License or consult a lawyer.
