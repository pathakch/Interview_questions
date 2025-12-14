### pip & pipenv


 1. Pipenv :

Way to install - Run this command in comman prompt, if python is already installed then pip will be available by default and pip will install this pipenv 

`pip install pipenv`

pipenv is python package manager tool, it automatically create a python virtual environment and activate it, This virtual env is not created inside project folder or working folder, it's created in system's user folder `C:\Users\<user>\.virtualenvs` and it's not visible to the developer because it does not apper in the project folder (also It looks confusing)
so to create this virtual environment inside project folder itself, run this command in command prompt `set PIPENV_VENV_IN_PROJECT=1` and then run `pipenv shell` or `pipenv install <lib_name>` it will create a virtual environment with name `.venv` inside project folder.

**Way to work with pipenv**

***Scenario.1*** 
- if creating any project from scratch meaning, open VS code and create each and every files from scratch
- 1. In this case, first of all open VS code, open command prompt and set `set PIPENV_VENV_IN_PROJECT=1` 
- 2. Run command `pipenv shell` it will create a virtual environment and activate, it will also create one pipfile
- 3. Run command `pipenv install <library_name>` - this comamnd will install the library inside .venv folder, write this in   `Pipfile` and then create one `pipfile.lock` file 
- 4. continue installing other libraries running `pipenv install <library_name>` - it will automatically capture it in `Pipfile` and `pipfile.lock` also automatically.

***Scenario.2*** 
- If checking out already existing project from git repo or from anywhere else
In this case that project may already contain `Pipfile` and `pipfile.lock` or `requirements.txt` then we just need to 
create a virtual environment inside project folder like previous scenario and then run `pipenv install` it will read `pipfile.lock` file and install all the libraries inside that virtual environment and keep working 

##### NOTE: 
- DO not create virtual environment using pipenv and then install libraries using pip, because it will install libraries in .venv but these libraries will not be captured in `Pipfile` and `pipfile.lock`.
- DO not do this : 
 1. pipenv shell 
 2. pip install requests  

 #### Difference between pip and pipenv

 pip and pipenv both are package management tools in python
 - 1. pip comes by default with python 
 - 2. pipenv - need to install pipenv with command `pip install pipenv`
 - 3. pipenv creates Pipfile and pipfile.lock automatically, pip does not do it
 - 4. after creating pipenv environment, it will automatically capture any new library installed by pipenv (pipenv install <lib_name>) in Pipfile and include that in pipfile.lock also.
 - 5. command to deactivate pip and pipenv are 'deactivate' & 'exit'
