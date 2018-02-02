# Intro to Data Analysis Notes

## Anaconda

### Conda Commands

#### Updating Conda and Packages

	conda update conda
	conda update --all
	conda update package_name
	
#### Installing and Removing Packages

	conda install package_name
	conda install numpy scipy pandas
	conda install numpy=1.10
	conda remove package_name
	
#### If you can't remember the name of a package or environment...
	conda list
	conda list env
	conda search search_term

#### Creating and Removing Environments

	conda create -n env_name list_of_packages
	conda create -n py3env python=3
	conda create -n py python=3.6
	conda env remove -n env_name
	
Most of the commands above can be used from within an environment to install or remove packages or update and search packages...
	
#### Entering and Leaving an Environment

##### On Mac / Linux
	
	source activate my_env
	source deactivate
	
##### On Windows

	activate my_env
	deactivate
	
#### Saving and Loading Environments

You can save the packages to a YAML file with 

	conda env export > environment.yaml
	
`> environment.yaml` writes the exported text to a YAML file environment.yaml. This file can now be shared and others will be able to create the same environment you used for the project.

To create an environment from an environment file use `conda env create -f environment.yaml`. This will create a new environment with the same name listed in environment.yaml.

#### Sharing environments

When sharing your code on GitHub, it's good practice to make an environment file and include it in the repository. This will make it easier for people to install all the dependencies for your code. I also usually include a pip requirements.txt file using pip freeze for people not using conda.