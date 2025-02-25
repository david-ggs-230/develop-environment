.. _install-vscode-typescript:

.. rst-class:: title-center h1
   
##################################################################################################
TypeScript in Visual Studio Code
##################################################################################################

**************************************************************************************************
Install Visual Studio Code
**************************************************************************************************

To install Visual Studio Code (VS Code) on your system, follow the steps below:

#. Download VS Code
    
    - Go to the official Visual Studio Code website: `https://code.visualstudio.com <https://code.visualstudio.com>`_
    - Click on the Download button. The website will automatically detect your operating system (Windows, macOS, or Linux).
    
#. Install VS Code on Windows
    
    - Run the Installer: Once the download is complete, run the installer (VSCodeSetup-x64-<version>.exe).
    - Accept the License Agreement: Follow the installation wizard. You will be prompted to accept the license agreement and choose the installation location.
    - Customize Installation: You can choose additional options such as creating desktop icons, adding to PATH, etc.
    - Complete Installation: Once you're ready, click Install and wait for the installation to complete.
    - Launch VS Code: After the installation, you can launch Visual Studio Code either from the Start Menu or directly from the desktop shortcut.
    
#. Verify the Installation. Open a terminal or command prompt and type ::
        
        code --version
        

**************************************************************************************************
Install Typescript to a project
**************************************************************************************************

To install TypeScript in a project, follow these steps:

#. Creating a new project folder
#. Navigate to the project folder
#. Initialize the project and generate a package.json file ::
    
    # npm
    npm init -y
    #yarn
    yarn init -y
    
#. Install TypeScript as a Development Dependency ::
    
    # npm
    npm install --save-dev typescript
    # yarn
    yarn add typescript --dev
    
#. Verify Installation ::
    
    # npm
    npx tsc --version
    # yarn
    yarn tsc --version
    
#. Create a TypeScript Configuration File ``tsconfig.json`` (Optional) ::
    
    # npm
    npx tsc --init
    # yarn
    yarn tsc --init
    
#. Create TypeScript Files ``.ts`` files
#. Compile TypeScript Code ::
    
    # npm
    npx tsc
    # npm compile a specific file app.ts
    npx tsc app.ts
    # yarn
    yarn tsc
    # yarn compile a specific file app.ts
    yarn tsc app.ts
   
#. Run the Compiled JavaScript Code, eg app.js ::
    
    # npm run app.js file
    node app.js
    # yarn
    node app.js
    

**************************************************************************************************
Install VSCode extensions
**************************************************************************************************

==================================================================================================
Adding linting to VSCode
==================================================================================================

Linting is the process of checking code for potential problems. It is common practice to use linting tools to catch problems early in the development process as code is written. ESLint is a popular tool that can lint React and TypeScript code. Editors such as Visual Studio Code can be integrated with ESLint to highlight potential problems.

Carry out the following steps to install an ESLint extension into Visual Studio Code:

#. Open up the Extensions area in Visual Studio Code
    
    - On ``Windows``: File > Preferences > Extensions
    - On ``macOS``: Code > Preferences > Extensions
    
#. Enter eslint into the extensions list search box
#. Select the ESLint extension by Microsoft
#. Click the Install button to install the extension.
#. Make sure the ESLint extension is configured to check typeScript and/or react/vue/html etc.
    
    - On ``Windows``: File > Preferences > Settings
    - On ``macOS``: Code > Preferences > Settings
        
        - In the settings search box, enter eslint: probe. This setting defines the languages to use when ESLint checks code. ::
            
            - Check User Tab
            - Check Workspace Tab
            
        - Check supported language ids. eg. javascript/typeScript/react/vue/html/typescriptreact
        - Using the ``Add Item`` button to add a specific language id.
        
    
#. For more information about ESLint, see the following link: https://eslint.org/.

==================================================================================================
Adding code formatting
==================================================================================================

Automatic code formatting ensures code is consistently formatted, which helps its readability. Having consistently formatted code also helps developers see the important changes in a code review – rather than differences in formatting. Prettier is a popular tool capable of formatting React and TypeScript code. 

--------------------------------------------------------------------------------------------------
Configure Prettier in the project
--------------------------------------------------------------------------------------------------

Carry out the following steps to install and configure Prettier in the project:

#. Install Prettier. Prettier is installed as a development dependency because it is only used during development time and not at runtime.
    
    .. code-block:: cfg
      :caption: Install Prettier
      :linenos:
      
      npm i -D prettier
      
    
#. Install the following two libraries (eslint-config-prettier and eslint-plugin-prettier) to allow Prettier to take responsibility for the styling rules from ESLint, as Prettier has overlapping style rules with ESLint:
    
    .. code-block:: cfg
      :caption: Install ESLint-Prettier
      :linenos:
      
      # eslint-config-prettier disables conflicting ESLint rules
      # eslint-plugin-prettier is an ESLint rule that formats code using Prettier.
      npm i -D eslint-config-prettier eslint-plugin-prettier
      
    
#. Update the eslintConfig section in package.json to allow Prettier to manage the styling rules as follows:
    
    .. code-block:: cfg
      :caption: eslintConfig section in package.json
      :linenos:
      
      {
        ...,
        "eslintConfig": {
            "extends": [
                ....,
                "plugin:prettier/recommended"
            ]
        },
        ...
      }
    
#. Create the Prettier conflicting file called .prettierrc.json.
    
    - Specified as follows:
        
        - Lines wrap at 100 characters
        - String qualifiers are single quotes
        - Semicolons are placed at the end of statements
        - The indentation level is two spaces
        - A trailing comma is added to multi-line arrays and objects
        - Existing line endings are maintained
        
    - 
        .. code-block:: cfg
          :caption: .prettierrc.json in the project root folder
          :linenos:
          
          {
              "printWidth": 100,
              "singleQuote": true,
              "semi": true,
              "tabWidth": 2,
              "trailingComma": "all",
              "endOfLine": "auto"
          }
    - More information on the configuration options can be found at the following link: https://prettier.io/docs/en/options.html.
    
#. Prettier is now installed and configured in the project.


--------------------------------------------------------------------------------------------------
Install Prettier – Code formatter in Visual Studio Code
--------------------------------------------------------------------------------------------------

Visual Studio Code can integrate with Prettier to automatically format code when source files are saved.

Carry out the following steps to install and configure a Prettier extension into Visual Studio Code:

#. Open up the Extensions area in Visual Studio Code
    
    - On ``Windows``: File > Preferences > Extensions
    - On ``macOS``: Code > Preferences > Extensions
    
#. Enter prettier into the extensions list search box
#. Select the ``Prettier – Code formatter`` extension by Prettier
#. Click the Install button to install the extension.
#. Open the Settings area in Visual Studio Code
    
    - On ``Windows``: File > Preferences > Settings
    - On ``macOS``: Code > Preferences > Settings
        
        - Setting Automatically Format Code On Save
            
            - Select the ``Workspace`` tab
            - Make sure the ``Format On Save`` option is ticked
            - This setting tells Visual Studio Code to automatically format code in files that are saved.
            
        - Setting Default Formatter to ``Prettier - Code formatter``
            
            - Select the ``Workspace`` tab
            - Find the ``Editor: Default Formatter`` option
            - Make sure Default Formatter is set to ``Prettier - Code formatter``
            - This is the default formatter that Visual Studio Code should use to format code
            
#. The Prettier extension for Visual Studio Code is now installed and configured in the project. 
