## Coding Standards in the Technology Facility Data Science Hub

This document serves as a set of best practices in terms of the tools and workflow that we think are sensible, widely-used, and relatively frictionless to use. They do not have to be adhered to, but we would suggest that if we are all working in a similar way then it makes it easier for us to collaborate, share workloads, and review each other's work.

The following guidelines will be an evolving thing that grows and changes as we start to put these into practice, and dependent on how the bits of software and standards that we've chosen to use change through time.

## VS Code - Our IDE of Choice for Developing Code

We would encourage you to use Microsoft's Visual Studio Code (VS Code) IDE when writing, developing, and running code. It is freely-available, built on an open-source foundation (although the distributed version is proprietary), and cross-platform. Visual Studio Code can be downloaded here: [https://code.visualstudio.com/](https://code.visualstudio.com/).

An IDE (Integrated Development Environment) like VS Code combines a text editor for writing code, with a terminal for running code, and a file browser for navigating and managing files and directories. This gives you everything you need to work effectively on a code-based project. Multiple files can be worked on simultaneously in different tabs, files can be dragged and dropped into different directories, or even from your file explorer straight into your current project. Code can be run as you write it, to ensure that it is working as intended.

VS Code has a powerful set of extensions, some developed by Microsoft and many developed by third party developers. Some of these are built into VS Code, like Git and GitHub integration (more on using Git for version control later), but most have to be installed through the Extensions Marketplace. Examples of very useful ones include code formatters and linters like Ruff and Black for automatically formatting and checking your code as you write it.

As well as working on local files and projects, VS Code allows you to connect to remote machines over SSH and work on files and directories of files in the same way that you would locally. This is extremely useful for working on HPC facilities like Viking, so you can avoid the pain of using a terminal-based text editor like Vim or Nano.