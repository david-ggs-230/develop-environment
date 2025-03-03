.. _install-python:

.. rst-class:: title-center h1
   
##################################################################################################
Python Environment
##################################################################################################

**************************************************************************************************
Install python
**************************************************************************************************
    
    - Visit the official Python download page and select an appropriate version to download.
    - Double-click the installer and follow the on-screen instructions. Don’t forget to check the "Add Python to PATH" option, which automatically adds Python's path to the PATH environment variable.
    - You can click "Install Now" for a standard installation; to customize the installation options, including choosing the installation path and configuring advanced options, select "Customize installation."
    - Verify Python installation
      
      .. code-block:: sh
        :linenos:
        
        # verify Python installation
        python --version
        python -V
        

**************************************************************************************************
Install Python PIP
**************************************************************************************************
    
    - Download the get-pip.py `https://bootstrap.pypa.io/get-pip.py <https://bootstrap.pypa.io/get-pip.py>`_ file
    - Run `python get-pip.py`
    - Run command
      
      .. code-block:: sh
        :linenos:
        
        # Install PIP
        python get-pip.py
        
        # PIP Verification
        pip -V
        pip --version
        
        # Update PIP
        python -m pip install --upgrade pip
        
        
**************************************************************************************************
Virtual Environment
**************************************************************************************************

==================================================================================================
Create Virtual Environment
==================================================================================================
    
    - Create the <project> folder.
    - Navigate to the <project> folder.
    - Use venv to create a virtual isolated environment.
    - Run command
      
      .. code-block:: sh
        :linenos:
        
        # Create a Python virtual environment
        # Create a .venv directory in the current directory
        python -m venv .venv
        

==================================================================================================
Activate the Virtual Environment
==================================================================================================
    
    .. code-block:: sh
       :linenos:
       
       # windows
       .venv\Scripts\activate.bat # activate the Python virtual environment
       

==================================================================================================
Install Packages
==================================================================================================
    
    .. code-block:: sh
       :linenos:
       
       # Installing py packages
       # windows
       pip install -i https://pypi.tuna.tsinghua.edu.cn/simple -U sphinx sphinx_rtd_theme myst-parser sphinx-autobuild sphinx-design
       

==================================================================================================
Generate requirements.txt file
==================================================================================================

--------------------------------------------------------------------------------------------------
Third-party Libraries requirements.txt
--------------------------------------------------------------------------------------------------

#. Open Terminal
#. Navigate to any folder
#. Generate all local environment dependencies.
#. pip freeze > requirements.txt
    
    .. code-block:: sh
       :linenos:
       
       # open terminal
       pip freeze > requirements.txt
       

--------------------------------------------------------------------------------------------------
Current Project requirements.txt
--------------------------------------------------------------------------------------------------

#. Open Terminal
#. Navigate to the <project> folder
#. To export the libraries used in the current project, navigate to the root directory of the project, then run the pipreqs ./ --encoding=utf8 command. This avoids encoding errors and automatically generates the requirements.txt file in the root directory.
#. pipreqs ./
    
    .. code-block:: sh
       :linenos:
       
       # Install pipreqs package
       pip install pipreqs
       # Export the libraries used in the current project to generate the requirements.txt.
       pipreqs ./
       # This command avoids encoding errors,
       pipreqs ./ --encoding=utf8
       
       

--------------------------------------------------------------------------------------------------
Install requirements.txt
--------------------------------------------------------------------------------------------------


#. It is best to create a new environment first to ensure isolation.
#. pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple 
    
    .. code-block:: sh
       :linenos:
       
       # Install requirements.txt
       pip install -r requirements.txt 
       # OR
       pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple 
       
**************************************************************************************************
Tutorial: Setting Up Python Virtual Environment
**************************************************************************************************

==================================================================================================
Activate Your Virtual Environment
==================================================================================================

    .. code-block:: sh
       :linenos:
       
       # Create a virtual environment 
       python -m venv myenv
       
       # Activate the virtual environment - Windows
       myenv\Scripts\activate
       # Activate the virtual environment - macOS and Linux
       source myenv/bin/activate
       

==================================================================================================
Install Dependencies
==================================================================================================

    .. code-block:: sh
       :linenos:
       
       # Install Dependencies
       pip install package-name
       # i.e. pip install pandas
       

==================================================================================================
Generate the requirements.txt File
==================================================================================================

    .. code-block:: sh
       :linenos:
       
       # Generate the requirements.txt File
       pip freeze > requirements.txt
       

==================================================================================================
Review your requirement.txt file
==================================================================================================

#. Open the requirement.txt in a text editor
#.

==================================================================================================
Generate requirements.txt in Python Using pipreqs
==================================================================================================
    pipreqs is a tool that generates a requirements.txt file for your Python project based on imports in your project and not just the packages installed in your Python environment. This often results in a cleaner and more accurate requirements.txt file.
    
--------------------------------------------------------------------------------------------------
Installing pipreqs
--------------------------------------------------------------------------------------------------

    .. code-block:: sh
       :linenos:
       
       # Installing pipreqs
       pip install pipreqs
       
--------------------------------------------------------------------------------------------------
Generating requirements.txt with pipreqs
--------------------------------------------------------------------------------------------------

    .. code-block:: sh
       :linenos:
       
       # Generating requirements.txt with pipreqs
       pipreqs /path/to/project
       
       # Force ignore .venv
       pipreqs --ignore .venv --force
       
==================================================================================================
Install Packages Using PIP With requirements.txt File in Python
==================================================================================================

    .. code-block:: sh
       :linenos:
       
       # Installing packages
       pip install -r requirements.txt -i https://xxxx
       

