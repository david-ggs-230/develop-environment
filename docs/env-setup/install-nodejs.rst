.. _install-nodejs:

.. rst-class:: title-center h1
   
##################################################################################################
NodeJS Environment
##################################################################################################

**************************************************************************************************
Node.js Installation
**************************************************************************************************

==================================================================================================
Install nvm
==================================================================================================

- Download the noinstall.zip file:
    
    - Visit the nvm-windows GitHub releases page: `nvm-windows releases <https://github.com/coreybutler/nvm-windows/releases>`_.
    - Download the `nvm-noinstall.zip <https://github.com/coreybutler/nvm-windows/releases/download/1.2.2/nvm-noinstall.zip>`_ file from the latest release.
    
- Extract the contents of noinstall.zip
    
    - Create a nvm installation folder <nvm-bin>
    - Extract downloaded zip file to the nvm installation folder <nvm-bin>
    
- Run the install.cmd Script
    
    - locate the ``install.cmd`` file
    - **Right-click** on ``install.cmd`` and select Run as administrator
    - After running the ``install.cmd`` script, close the current command prompt and open a new one so the environment variables take effect.
    
- Verify installation ::
    
    nvm -v
    nvm version
    nvm --version
    
- nvm usage
    
    .. code-block:: sh
      :linenos:
      
      # Displays whether Node.js is running in 32-bit or 64-bit mode
      nvm arch
      # Shows the list of installed Node.js versions
      nvm list [available]
      nvm ls [available]
      # Installs a specific version of Node.js. Example: nvm install 16.14.0
      nvm install <version>
      # Enables Node.js version management (activates nvm).
      nvm on
      # Disables Node.js version management (deactivates nvm).
      nvm off
      # Sets a download proxy for installing Node.js versions.
      nvm proxy [url]
      # Sets the Node.js mirror URL. The default URL is https://nodejs.org/dist/
      nvm node_mirror [url]
      # Sets the NPM mirror URL. The default URL is https://github.com/npm/cli/archive/.
      nvm npm_mirror [url]
      # Uninstalls the specified version of Node.js.
      nvm uninstall <version>
      # Switches to a specific Node.js version.
      nvm use [version]
      # Sets the directory where Node.js versions are stored. If not set, it defaults to the current directory.
      nvm root [path]
      # Displays the installed version of nvm
      nvm version 
      # Set the default Node version
      nvm alias default <version>
      
==================================================================================================
Setup NodeJS Mirror
==================================================================================================
    
    Edit settings.txt file ::
        
        # root folder for nvm.exe
        root: <nvm-noninstall-folder>
        # node.exe shortcut path
        path: <node.exe shotcut path>
        
        # Sets the Node.js mirror URL
        nvm node_mirror https://npmmirror.com/mirrors/node/
        # Sets the NPM mirror URL
        nvm npm_mirror https://npmmirror.com/mirrors/npm/
        

==================================================================================================
Install NodeJS
==================================================================================================
    
    .. code-block:: sh
        :linenos:
        
        # Shows the list of available Node.js versions
        nvm ls available
        
        # Shows the list of installed Node.js versions
        nvm ls
        
        # Install a specific version of Node.js, eg. nvm install 22.14.0
        nvm install <version>
        
        # Switches to a specific Node.js version.
        nvm use [version]
        
        # Check node and npm version
        node -v && npm -v
        
**************************************************************************************************
Node Package Manager
**************************************************************************************************

==================================================================================================
NPM 
==================================================================================================

The Node.js Package Manager (npm) is the default package manager for Node.js and is used for managing JavaScript libraries and tools. With npm, you can install, update, configure, and remove packages (libraries) for your Node.js projects.

- To verify that npm is installed 
    
    .. code-block:: sh
        
        npm -v
        
- Install a Package Locally 
    
    .. code-block:: sh
        
        npm install <package-name>
        # Add to project's package.json dependencies
        npm install --save <package-name>
        npm install -S <package-name>
        # Add to project's package.json devDependencies
        npm install --save-dev <package-name>
        npm install -D <package-name>
        
        
- Install a Local Package file 
    
    .. code-block:: sh
        
        # Install local .tgz file
        npm install <package-file.tgz>
        
- Install a Package Globally 
    
    .. code-block:: sh
        
        npm install -g <package-name>
        
- Install different version of a package. This allows you to install a package, but refer to it by a different name in your project.
    
    .. code-block:: sh
        
        npm install <alias>@npm:<name>
        # eg.
        #    npm install lodash3@npm:lodash@3
        #    npm install lodash4@npm:lodash@4
        # usage:
        #    const lodash3 = require('lodash3');
        #    const lodash4 = require('lodash4');
        # Another example:
        # 
        # Install the lodash package but alias it as utility in package.json
        #    npm install utility@npm:lodash
        # Usage:
        #    require('utility')
        #    import utility from 'utility'
        
- Start a Node.js project, creating a package.json file and keeping track of the project’s dependencies 
    
    .. code-block:: sh
        
        # To create a package.json file
        npm init
        # Generate the package.json with default values
        npm init -y 
        
- Install all dependencies for a project 
    
    .. code-block:: sh
        
        npm install
        
- Update a package to the latest version 
    
    .. code-block:: sh
        
        npm update <package-name>
        
- Update all packages listed in the project package.json file 
    
    .. code-block:: sh
        
        npm update
        
- Uninstall a specific package 
    
    .. code-block:: sh
        
        npm uninstall <package-name>
        
- Uninstall and remove the package from the package.json file 
    
    .. code-block:: sh
        
        npm uninstall <package-name> --save
        
- Check for outdated packages 
    
    .. code-block:: sh
        
        npm outdated
        
- List all packages installed in the project 
    
    .. code-block:: sh
        
        npm list
        npm ls
        
- List globally installed packages 
    
    .. code-block:: sh
        
        npm list -g
        
- Install a specific version of a package 
    
    .. code-block:: sh
        
        npm install <package-name>@<version>
        
- Search for a package 
    
    .. code-block:: sh
        
        npm search <package-name>
        
- Get help 
    
    .. code-block:: sh
        
        npm help
        
- Get help for specific commands, like install 
    
    .. code-block:: sh
        
        npm help install
        
-  View all the available metadata about a package, npm view <package-name> [<field>]
    
    .. code-block:: sh
        
        npm view <package-name>
        npm view <package-name> version
        npm view <package-name> versions
        npm view <package-name> dependencies
        npm view <package-name> description
        npm view <package-name> repository
        npm view <package-name> author
        npm view <package-name> bugs
        npm view <package-name> license
        npm show <package-name> version
        
- Configure registry
    
    .. code-block:: sh
        
        # change registry
        npm config set registry https://registry.npmmirror.com
        # check registry
        npm config get registry
        # clean cache
        npm cache clean --force
        
==================================================================================================
YARN 
==================================================================================================

Yarn is a popular package manager for JavaScript, created by Facebook to address some of the shortcomings of npm (Node Package Manager). Yarn provides fast, reliable, and secure dependency management for JavaScript and Node.js projects. It is widely used in modern web development, particularly with frameworks like React, Vue, and Angular.

- Install Yarn
    
    .. code-block:: sh
        
        # Using npm
        npm install -g yarn
        # Using Homebrew (macOS)
        brew install yarn
        # Using Linux (Debian/Ubuntu)
        sudo apt install yarn
        
- To check which version of Yarn is installed
    
    .. code-block:: sh
        
        yarn --version
        
- To initialize a new project and create a package.json file 
    
    .. code-block:: sh
        
        # To create a package.json file
        yarn init
        # Generate the package.json with default values
        yarn init -y
        
- To install the dependencies listed in package.json file 
    
    .. code-block:: sh
        
        yarn install
        
- To install a new package and add it as a dependency 
    
    .. code-block:: sh
        
        yarn add <package-name>
        
- To install a package as a devDependency
    
    .. code-block:: sh
        
        yarn add <package-name> --dev
        
- To install a specific version
    
    .. code-block:: sh
        
        yarn add <package-name>@<version>
        
- To install a package globally
    
    .. code-block:: sh
        
        yarn global add <package-name>
        
- To remove a package from the project
    
    .. code-block:: sh
        
        yarn remove <package-name>
        
- To remove a globally installed package
    
    .. code-block:: sh
        
        yarn global remove <package-name>
        
- To upgrade all dependencies to their latest versions
    
    .. code-block:: sh
        
        yarn upgrade
        
- To upgrade a specific package
    
    .. code-block:: sh
        
        yarn upgrade <package-name>
        
- To list all installed packages in the current project
    
    .. code-block:: sh
        
        yarn list
        
- To list global packages
    
    .. code-block:: sh
        
        yarn global list
        
- Check for outdated packages 
    
    .. code-block:: sh
        
        yarn outdated
        
- Run a script from package.json 
    
    .. code-block:: sh
        
        yarn <script-name>
        
- To view the cache 
    
    .. code-block:: sh
        
        yarn cache list
        
- To clean the cache
    
    .. code-block:: sh
        
        yarn cache clean
        
