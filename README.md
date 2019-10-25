# GlobusContentsManager (WIP)
A Globus backed ContentsManager implementation for Jupyter Notebook.

## Prerequisites
* An app registered with Globus. See the [Globus Auth Developer Guide](https://docs.globus.org/api/auth/developer-guide/) if you are unfamiliar with the Globus app registration process.
* The project's default settings uses the Globus Tutorial Endpoints, so you must be a member of the [Tutorial Users Group](https://app.globus.org/groups/50b6a29c-63ac-11e4-8062-22000ab68755)
* A local Globus Connect Personal (GCP) instance. If you do not havve one, see the instructions below for your corresponding operating system:
    * [Mac OS X](https://docs.globus.org/how-to/globus-connect-personal-mac)
    * [Windows](https://docs.globus.org/how-to/globus-connect-personal-windows)
    * [Linux](https://docs.globus.org/how-to/globus-connect-personal-linux)

## Installation
**Note**: At this time, the project must be installed locally.

#### Clone the repo
`$ git clone https://github.com/gneezyn/globus-contents-manager.git`

#### Install the GlobusContentsManager
`$ pip install globus-contents-manager`

#### Jupyter config setup
This step is needed so that Jupyter knows to use the GlobusContentsManager instead of the default ContentsManager. There are two approaches that you can take for configuring Jupyter to work with the GlobusContentsManager.

##### Option 1: Use a local jupyter notebook config file
This approach is best used if you want to use the simplest (default) configuration options or if you want to easily be able to switch between multiple Jupyter Notebook configurations. 
* Go to the `jupyter_notebook_config.py` file located in the root directory and make the following changes:
    * `c.NotebookApp.contents_manager_class.globus_local_endpoint = '<endpoint_id>'` where `<endpoint_id>` is the ID of your local GCP Endpoint
        * Example: `c.NotebookApp.contents_manager_class.globus_local_endpoint = '71303c92-eeab-11e9-be8e-02fcc9cdd752'`
* To start the notebook, run the command: `$ jupyter notebook --config=<file>`
    * `<file>` should be replaced by the path of your local config file
    * Example: `$ jupyter notebook --config=jupyter_notebook_config.py`

##### Option 2: Edit `~/.jupyter/jupyter_notebook_config.py`
This approach is best used if you want Jupyter to always use the GlobusContentsManager when you open a new or existing Jupyter Notebook. 

1. Edit or generate the `jupyter_notebook_config.py` file in the `~/.jupyter/` directory and make sure that it correctly specifies the GlobusContentsManager.
    * The `jupyter_notebook_config.py` file located in the root directory of this project provides an example of what the basic setup for this project would look like. 
        * See **Option 1** for instructions on what changes to make.
    * To generate a `jupyter_notebook_config.py` file, with all of the defaults commented out, run the following command: `$ jupyter notebook --generate-config`
    * You can refer to the [Jupyter Config Documentation](https://jupyter-notebook.readthedocs.io/en/stable/config.html) for more details on the different options (not including the ones specific to the GlobusContentsManager) available.
2. Start the Jupyter Notebook: `jupyter notebook`