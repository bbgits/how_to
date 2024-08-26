
# Getting Started
**Display currently active python env:**  
`which python`

**Display packages for current env:**  
`pip3 list`






**Linux, prerequisite:**  
On Debian/Ubuntu systems, you need to install the python3-venv package using the following command:  
`sudo apt install python3.12-venv`


**create virtual environment named 'project_env':**  
`python3 -m venv project_env`
- this envrionment will use the same version of python that this venv was created with.
- 

**activate virtual environment**  
`source project_env/bin/activate`
- at this point, you should see (project_env) as a prefix in your terminal, indicating that the virtual environment is active
- you can verify by displaying the currently active python version (`which python`) or by listing the currently installed packages (`pip3 list`)
- any packages you install using `pip instal [package]` will be installed on this virtual environment.


# Notes
- for venvs, use `python` instead of `python3`