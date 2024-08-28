---
type: "docs"
draft: false
title: Conda
author: "dpak94"
---

# Conda

| Action                                                       | Command                                  |
| ------------------------------------------------------------ | ---------------------------------------- |
| list all environments and locations                          | `conda env list`                         |
| update all packages in environment                           | `conda update --all --name ENVNAME`      |
| install packages in environment                              | `conda install --name ENVNAME PKG1 PKG2` |
| remove package from environment                              | `conda uninstall PKGNAME --name ENVNAME` |
| reactivate base environment (recommended for end of session) | `conda activate base`                    |

**Environment Management**

| Action                                  | Command                                          |
| --------------------------------------- | ------------------------------------------------ |
| list packages + source channels         | `conda list -n ENVNAME --show-channel-urls`      |
| uninstall package from specific channel | `conda remove -n ENVNAME -c CHANNELNAME PKGNAME` |
| create environment with Python version  | `conda create -n ENVNAME python=3.10`            |
| clone environment                       | `conda create --clone ENVNAME -n NEWENV`         |
| list revisions made to environment      | `conda list -n ENVNAME --revisions`              |
| restore environment to a revision       | `conda install -n ENVNAME --revision NUMBER`     |
| delete environment by name              | `conda remove -n ENVNAME --all`                  |

**Exporting Environments**

| Action                                | Command                                   |
| ------------------------------------- | ----------------------------------------- |
| cross-platform compatible             | `conda env export --from-history>ENV.yml` |
| platform + package specific           | `conda env export ENVNAME>ENV.yml`        |
| platform + package + channel specific | `conda list --explicit>ENV.txt`           |

**Importing Environments**

| Action                  | Command                                      |
| :---------------------- | :------------------------------------------- |
| Import from a .yml file | `conda env create -n ENVNAME --file ENV.yml` |
| Import from a .txt file | `conda create -n ENVNAME --file ENV.txt`     |

**Additional Commands**

| Action                                                        | Command                                                       |
| ------------------------------------------------------------- | :------------------------------------------------------------ |
| get help for any command                                      | `conda COMMAND --help`                                        |
| get info for any package                                      | `conda search PKGNAME --info`                                 |
| run commands w/o user prompt eg, installing multiple packages | `conda COMMAND ARG --yes </br> conda install PKG1 PKG2 --yes` |
| remove all unused files                                       | `conda clean --all`                                           |
| examine conda configuration                                   | `conda config --show`                                         |
