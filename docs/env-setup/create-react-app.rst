.. _create-react-app:

.. rst-class:: title-center h1
   
##################################################################################################
Create a React App
##################################################################################################

**************************************************************************************************
Create a React App with Vite
**************************************************************************************************

==================================================================================================
Prerequisites
==================================================================================================
    
    Vite requires Node.js version ≥ 18. and npm version 8. However, some templates require a higher Node.js version to work.
        
        - Node version ≥ 18.
        - NPM version 8.
        

==================================================================================================
Create Vite Project
==================================================================================================
    
    Create a React project using Vite with a single command ::
        
        # npm
        npm create vite@latest my-app -- --template react
        # yarn
        yarn create vite my-app --template react
        

==================================================================================================
Install dependencies and run the project
==================================================================================================
    
    - Navigate to the project directory ::
        
        cd my-app
        
    - Install the dependencies ::
        
        # npm
        npm install
        # yarn 
        yarn install
        
    - Start the project ::
        
        #The application is running at http://localhost:5173
        # npm
        npm run dev
        # yarn
        yarn run dev
        
    - Build the app ::
        
        # npm
        npm run build
        # yarn
        yarn run build
        
    - Testing the built app locally ::
        
        # npm
        npm run preview
        # yarn
        yarn run preview
        

==================================================================================================
ESLint configuration (Optional)
==================================================================================================

ESLint is a popular, open source linter for JavaScript. Install ESLint with the recommended configuration for React ``eslint-config-react-app``. This package includes the shareable ESLint configuration used by Create React App. This configuration is used by Create React App, which includes it by default. This config also ships with optional Jest rules for ESLint (based on eslint-plugin-jest). If you want to use this ESLint configuration in a project not built with Create React App, you can install it with the following steps: 
    
    - Install this package and ESLint ::
        
        npm install --save-dev eslint-config-react-app eslint@^8.0.0
        
    - Create a file named .eslintrc.json with following contents in the root folder of the project:
        
        .. code-block:: cfg
          :caption: contents of .eslintrc.json
          :linenos:
          
          {
              "extends": "react-app"
          }
          
    - Enable optional Jest rules for ESLint 
        
        .. code-block:: cfg
          :caption: contents of .eslintrc.json
          :linenos:
          
          {
              "extends": ["react-app", "react-app/jest"]
          }
          

**************************************************************************************************
Create Next.js-powered React App
**************************************************************************************************

==================================================================================================
Prerequisites
==================================================================================================
    
    System requirements:
        
        - Node.js 18.18 or later.
        - macOS, Windows (including WSL), and Linux
        

==================================================================================================
Create a new Next.js project
==================================================================================================
    
    Create a new Next.js project with a single command. To set up a new project non-interactively, pass command line arguments. ::
        
        # npx create-next-app@latest <react-app-name>
        npx create-next-app@latest
        npx create-next-app@latest my-app --js --yes
        npx create-next-app@latest my-app --ts --yes
        # yarn create next-app <react-app-name>
        yarn create next-app my-app --js --src-dir --use-yarn --yes
        yarn create next-app my-app --ts --src-dir --use-yarn --yes
        
    
    Usage: create-next-app [project-directory] [options] ::
        
        Options:
          -V, --version                        output the version number
          --ts, --typescript
        
            Initialize as a TypeScript project. (default)
        
          --js, --javascript
        
            Initialize as a JavaScript project.
        
          --tailwind
        
            Initialize with Tailwind CSS config. (default)
        
          --eslint
        
            Initialize with ESLint config.
        
          --app
        
            Initialize as an App Router project.
        
          --src-dir
        
            Initialize inside a `src/` directory.
        
          --turbopack
        
            Enable Turbopack by default for development.
        
          --import-alias <alias-to-configure>
        
            Specify import alias to use (default "@/*").
        
          --empty
        
            Initialize an empty project.
        
          --use-npm
        
            Explicitly tell the CLI to bootstrap the application using npm
        
          --use-pnpm
        
            Explicitly tell the CLI to bootstrap the application using pnpm
        
          --use-yarn
        
            Explicitly tell the CLI to bootstrap the application using Yarn
        
          --use-bun
        
            Explicitly tell the CLI to bootstrap the application using Bun
        
          -e, --example [name]|[github-url]
        
            An example to bootstrap the app with. You can use an example name
            from the official Next.js repo or a GitHub URL. The URL can use
            any branch and/or subdirectory
        
          --example-path <path-to-example>
        
            In a rare case, your GitHub URL might contain a branch name with
            a slash (e.g. bug/fix-1) and the path to the example (e.g. foo/bar).
            In this case, you must specify the path to the example separately:
            --example-path foo/bar
        
          --reset-preferences
        
            Explicitly tell the CLI to reset any stored preferences
        
          --skip-install
        
            Explicitly tell the CLI to skip installing packages
        
          --disable-git
        
            Explicitly tell the CLI to skip initializing a git repository.
        
          --yes
        
            Use previous preferences or defaults for all options that were not
            explicitly specified, without prompting.
        
          -h, --help                           display help for command
     
     
==================================================================================================
Install dependencies and run the project
==================================================================================================
    
    - Navigate to the project directory ::
        
        cd my-app
        
    - Install the dependencies ::
        
        # npm
        npm install
        # yarn 
        yarn install
        
    - Start the project ::
        
        #The application is running at http://localhost:5173
        # npm
        npm run dev
        # yarn
        yarn run dev
        
    - Build the app ::
        
        # npm
        npm run build
        # yarn
        yarn run build
        
