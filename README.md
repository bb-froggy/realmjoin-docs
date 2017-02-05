# RealmJoin Technical Documentation Contributor Guide
You've found the GitHub repository that houses the source for the RealmJoin technical documentation that is published on [https://realmjoin.readthedocs.org](https://realmjoin.readthedocs.org).

This repository also contains guidance to help you contribute to our technical documentation. 

## Contribute to RealmJoin documentation
Thank you for your interest in RealmJoin documentation!

* [Ways to contribute](#ways-to-contribute)
* [About your contributions to RealmJoin content](#about-your-contributions-to-realmjoin-content)
* [Repository organization](#repository-organization)
* [Use GitHub, Git, and this repository](#use-github-git-and-this-repository)
* [How to use markdown to format your topic](#how-to-use-markdown-to-format-your-topic)
* [More resources](#more-resources)

## Ways to contribute
You can submit updates to the [RealmJoin documentation](https://realmjoin.readthedocs.org) as follows:

* You can easily contribute to technical articles in the GitHub user interface. Either find the article in this repository, or visit the article on [https://realmjoin.readthedocs.org](https://realmjoin.readthedocs.org) and click the link in the article that goes to the GitHub source for the article.
* If you are making substantial changes to an existing article, adding or changing images, or contributing a new article, you need to fork this repository, install Git Bash, Markdown Pad, and learn some git commands.

## About your contributions to RealmJoin content
### Minor corrections
Minor corrections or clarifications you submit for documentation and code examples in this repo are covered by the general terms of use.

### Larger submissions
If you submit a pull request with new or significant changes to documentation and code examples, we'll send a comment in GitHub asking you to submit an online Contribution License Agreement (CLA) if you are not an employee of Glück & Kanja. We need you to complete the online form before we can accept your pull request.

## Repository organization
The content in the docs repository follows the organization of documentation on https://realmjoin.readthedocs.org. This repository contains two root folders:

### \docs
The \*docs* folder contains the documentation articles formatted as markdown files with an *.md* extension.

The \*docs* folder contains the \*media* folder for root directory article media files, inside which are subfolders with the images for each article.  The service folders contain a separate media folder for the articles within each service folder. The article image folders are named identically to the article file, minus the *.md* file extension.

### \contributor-guide
This folder contains articles that are part of our contributors' guide.

## Use GitHub, Git, and this repository
For information about how to contribute, how to use the GitHub UI to contribute small changes, and how to fork and clone the repository for more significant contributions, see [Install and set up tools for authoring in GitHub](https://github.com/Microsoft/azure-docs/blob/master/contributor-guide/tools-and-setup.md).

If you install GitBash and choose to work locally, the steps for creating a new local working branch, making changes, and submitting the changes back to the main branch are listed in [Git commands for creating a new article or updating an existing article](https://github.com/Microsoft/azure-docs/blob/master/contributor-guide/git-commands-for-master.md)

### Branches
We recommend that you create local working branches that target a specific scope of change. Each branch should be limited to a single concept/article both to streamline work flow and reduce the possibility of merge conflicts.  The following efforts are of the appropriate scope for a new branch:

* A new article (and associated images)
* Spelling and grammar edits on an article.
* Applying a single formatting change across a large set of articles (e.g. new copyright footer).

## How to use markdown to format your topic
All the articles in this repository use GitHub flavored markdown.  Here's a list of resources.

* [Markdown basics](https://help.github.com/articles/markdown-basics/)
* [Printable markdown cheatsheet](https://github.com/Microsoft/azure-docs/blob/master/contributor-guide/media/documents/markdown-cheatsheet.pdf?raw=true)

## More resources
See the [Index of Microsoft Contributor's Guide](https://github.com/Microsoft/azure-docs/blob/master/contributor-guide/contributor-guide-index.md) for more guidance topics.

(based on [Microsoft Contributor's Guide](https://github.com/Microsoft/azure-docs))
