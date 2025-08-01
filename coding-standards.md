## Coding Standards in the Technology Facility Data Science Hub

This document serves as a set of best practices in terms of the tools and workflow that we think are sensible, widely-used, and relatively frictionless to use. They do not have to be adhered to, but we would suggest that if we are all working in a similar way then it makes it easier for us to collaborate, share workloads, and review each other's work.

The following guidelines will be an evolving thing that grows and changes as we start to put these into practice, and dependent on how the bits of software and standards that we've chosen to use change through time.

## Key points

* Use Visual Studio Code as your IDE of choice
* Maintain codebases with Git and GitHub
* Use the Ruff formatter/linter to standardise your code and conform with PEP 8
* Use uv for developing and managing Python codebases

## VS Code - Our IDE of Choice for Developing Code

We would encourage you to use Microsoft's Visual Studio Code (VS Code) IDE when writing, developing, and running code. It is freely-available, built on an open-source foundation (although the distributed version is proprietary), and cross-platform. Visual Studio Code can be downloaded here: [https://code.visualstudio.com/](https://code.visualstudio.com/).

An IDE (Integrated Development Environment) like VS Code combines a text editor for writing code, with a terminal for running code, and a file browser for navigating and managing files and directories. This gives you everything you need to work effectively on a code-based project. Multiple files can be worked on simultaneously in different tabs, files can be dragged and dropped into different directories, or even from your file explorer straight into your current project. Code can be run as you write it, to ensure that it is working as intended.

VS Code has a powerful set of extensions, some developed by Microsoft and many developed by third party developers. Some of these are built into VS Code, like Git and GitHub integration (more on using Git for version control later), but most have to be installed through the Extensions Marketplace. Examples of very useful ones include code formatters and linters like Ruff and Black for automatically formatting and checking your code as you write it.

As well as working on local files and projects, VS Code allows you to connect to remote machines over SSH and work on files and directories of files in the same way that you would locally. This is extremely useful for working on HPC facilities like Viking, so you can avoid the pain of using a terminal-based text editor like Vim or Nano.

## Version control with Git and GitHub

Version control is an essential part of managing your code, giving you flexibility in how you develop it, a built-in edit history, and the ability to collaborate more easily on a single codebase. Our version control software of choice is [git](https://git-scm.com/).

Git is a free and open-source version control system. It tracks changes to files/directories and allows "commits" to be made to capture the state of the files/directories at a given point in time. Branches, to develop particular features or bug-fixes for example, can be made from the main branch of your code and then merged back in when that feature is completed, amongst many other features.

Git works on local files/directories on a machine, but a remote git repository can be used to push/pull code to and from. The most popular of these is [GitHub](https://github.com/), and this is the one that we use. There are many others such as GitLab, Gitea, etc., all of which work in a very similar way. Think of these as a secure remote place you can store your code and all of its associated Git history, allowing others to access and work on it alongside you.

A basic, minimal set of best practices for Git/GitHub that we would suggest are:

1. Always have a LICENSE file in the top level of your repository. My preferred license is the MIT license.
2. Always have a README.md file in the top level of your repository with a minimal set of instructions on what the code is, how to install it, and how to use it.
3. Always commit to branches and then submit pull requests to your main branch, rather than commiting straight to main.
4. Makes commits often. It will your life much easier in the event that something goes wrong.

## Code standards and formatting

A majority of our code is written in the Python programming language. Python has its own style guide for writing Python code, called PEP 8, which gives recommendations for standards that should be used for well-written Python. This is exhaustive, and covers things such as indentation, line lengths, function and class name conventions, and much more besides.

We would suggest complying with PEP 8. It makes your code more readable to others, and makes coding collaboratively more straightforward. You can read the PEP 8 Python style guide here: [https://peps.python.org/pep-0008/](https://peps.python.org/pep-0008/).

A formatter will either automatically or manually make the formatting of the code that you write compliant with a standard like PEP 8. An example of a code formatter would be the [Black code formatter](https://github.com/psf/black) for Python. It will reformat your code to make it compliant with PEP 8, and gives you little control over how it does this.

A linter is similar, but subtly different, in that it will also make your code compliant with a standard like PEP 8 but, in addition, it will identify errors and other potential issues with your code (unused variables, imports, etc.). An example of a Python linter would be [Flake8](https://flake8.pycqa.org/en/latest/).

We would suggest using [Ruff](https://docs.astral.sh/ruff/). Ruff is a combined code formatter and linter for Python, and does the combined jobs of Black and Flake8, i.e. both reformatting your code _and_ flagging errors and warnings relating to the code that you've written.

There is an official Ruff extension for VS Code, made by Astral (the developers of Ruff) and when installed it will automatically format and lint your code as you write it. It can be configured (through the VS Code configuration) in lots of different ways, to only reformat when saved, to do different levels of linting, etc.

It's important to realise that using something like Ruff isn't an excuse to be lazy and write poorly-formatted code, and that it won't fix or identify every error in your code, but it can i) pick up small formatting issues that you may have missed, and ii) identify a lot of basic errors in your code before actually running the code, when it actually matters.

## Developing Python code with uv

When developing any code, not just Python code, common issues you will hit up against are:

* installing and managing library dependencies that your code relies upon
* ensuring that your code, and any dependencies, do not impact on other code/software on your system
* packaging up and distributing your code

Traditionally, these tasks would all require separate tools, like pip for installing dependencies, virtualenv for creating virtual environments to develop and test you code in, and something like setuptools to package up your code and send it to PyPI or equivalent.

uv (you can read more about uv in the documentation here: [https://docs.astral.sh/uv/](https://docs.astral.sh/uv/)]) succeds at replacing all of these tasks and separate tools with a single tool to develop and distribute your code, and does so extremely quickly and efficiently. It is a fast, single, cross-platform tool that you can use to build your Python code from end-to-end.

Once initialised as a uv project, a directory becomes its own walled-off virtual environment into which Python library dependencies can be added (i.e. installed). These dependencies can be "locked", meaning that their version and any of their own dependencies' versions are locked down and should therefore be installable on other systems.

Rather than having to be activated and deactivated like other virtual environments, commands can be run in your project's uv environment simply by pre-pending `uv run` to the command, e.g. `uv run python3 hello-world.py`.

Your package can be published to PyPI simply by running `uv publish` within its project directory.

Much of the above functionality depends upon a `pyproject.toml` file which contains details of your project's name, version, module files and scripts, dependencies, etc., but we will not go into detail about that here. You can read more about configuring your uv project and the pyproject.toml file here: [https://docs.astral.sh/uv/concepts/projects/config/](https://docs.astral.sh/uv/concepts/projects/config/).