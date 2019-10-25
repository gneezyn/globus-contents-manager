# Project Structure
This document describes this project's structure and explains the purpose of the various files and directories.

## Overview
The following are general descriptions of the different files and directories in the project. Certain generic files and directories (i.e., requirements.txt, ipycompat.py, docs, etc.) are not included.

**globus-contents-manager**: the root directory of the project (this may differ for you if you check it out under a different name)
* **globuscontents**: the main directory that contains all of the files and directories relevant to the `GlobusContentsManager`
    * **globus_contents_manager.py**: defines a custom ContentsManager with Globus functionality
    * **scripts**: a directory for useful python scripts (only has one script at this time and might be removed in the future)
        * **tokens_script.py**: a python script that spawns tokens (for Globus Auth); possibly redundant at this point
    * **utils.py**: contains various useful functions
* **jupyter_notebook_config.py**: an example of the file that tells Jupyter Notebook to use the `GlobusContentsManager`