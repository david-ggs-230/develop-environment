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
        npm create vite@latest my-app -- --template react-ts
        # yarn
        yarn create vite my-app --template react
        yarn create vite my-app --template react-ts
        

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
Hosting the React App on GitHub Pages
==================================================================================================
    
    - Creating a github repo, ``main`` branch
    - Create a ``gh-pages`` branch
    - Enable GitHub Pages by configuring ``Settings`` -> ``Pages``
    - Create the deploying base folder in the ``gh-pages`` branch
        
        - if deploying to `https://<USERNAME>.github.io/<repo-name>/<deploying-base-dir>/<sub-dir>/ <https://\<USERNAME\>.github.io/\<repo-name\>/\<deploying-base-dir\>/\<sub-dir\>/>`_, then create:
            
            - in the ``gh-pages`` branch, create ``/<repo-name>/<deploying-base-dir>/<sub-dir>/`` folder structure
            - upload the build files to `https://github.com/<USERNAME>/<repo-name>/<deploying-base-dir>/<sub-dir>/ <https://github.com/\<USERNAME\>/\<repo-name\>/\<deploying-base-dir\>/\<sub-dir\>/>`_ in the ``gh-pages`` branch
            - the deploying base is ``/<repo-name>/<deploying-base-dir>/<sub-dir>/``
            - the deploying url: ``https://<USERNAME>.github.io/<repo-name>/<deploying-base-dir>/<sub-dir>/``
            
        - Configure the build base url:
            
            - open vite.config.js file
            - set base to ``/<repo-name>/<deploying-base-dir>/<sub-dir>/`` ::
                
                export default defineConfig({
                    plugins: [react()],
                    base: '/<repo-name>/<deploying-base-dir>/<sub-dir>/',
                })
                
    - Build the app ::
        
        # npm
        npm run build
        # yarn
        yarn run build
        
    - Push the <dist> folder contents to the deploying base folder in the ``gh-pages`` branch
    

==================================================================================================
Install EditorConfig for VS Code (Optional)
==================================================================================================

EditorConfig (https://editorconfig.org) is picked up by IDEs to alter their default behavior (e.g. make IDEs put the right tab size when you press TAB or always add a new line at the end of the file on save). It attempts to override user/workspace settings with settings found in .editorconfig files. No additional or vscode-specific files are required. As with any EditorConfig plugin, if root=true is not specified, EditorConfig will continue to look for an .editorconfig file outside of the project.

#. Add .editorconfig (https://editorconfig.org) to the root of the project ::
    
    root = true
    
    [*]
    indent_style = space
    indent_size = 2
    end_of_line = lf
    insert_final_newline = true
    trim_trailing_whitespace = true
    
#. Reload VS Code (open the command palette, find and use “Reload Window”).

==================================================================================================
ESLint and Prettier configuration (Optional)
==================================================================================================

Reference: `Setup ReactJS typescript project with vite, eslint, and prettier 2024 by Josprima, 
Aug 20, 2024 <https://medium.com/@josprima.id/setup-reactjs-typescript-project-with-vite-eslint-and-prettier-2024-e714f7daca1a>`_ 

Linting is the process of checking code for potential problems. It is common practice to use linting tools to catch problems early in the development process as code is written. ESLint is a popular tool that can lint React and TypeScript code. 

Automatic code formatting ensures code is consistently formatted, which helps its readability. Having consistently formatted code also helps developers see the important changes in a code review – rather than differences in formatting. Prettier is a popular tool capable of formatting React and TypeScript code.

    
    - Install dependencies ::
        
        # npm
        npm install --save-dev prettier eslint-plugin-prettier eslint-config-prettier  eslint-plugin-react
        # yarn
        yarn add --dev prettier eslint-plugin-prettier eslint-config-prettier  eslint-plugin-react 
        
    - Modify the eslint.config.js file with following contents: 
        
        .. code-block:: cfg
          :caption: contents of eslint.config.js
          :linenos:
          
          import js from "@eslint/js";
          import globals from "globals";
          import reactHooks from "eslint-plugin-react-hooks";
          import reactRefresh from "eslint-plugin-react-refresh";
          import tseslint from "typescript-eslint";
          import react from "eslint-plugin-react";
          import eslintPluginPrettier from "eslint-plugin-prettier/recommended";
          
          export default tseslint
            .config(
              { ignores: ["dist"] },
              {
                //extends: [js.configs.recommended, ...tseslint.configs.recommended],
                extends: [
                  js.configs.recommended,
                  ...tseslint.configs.recommendedTypeChecked,
                ],
                files: ["**/*.{ts,tsx}"],
                languageOptions: {
                  ecmaVersion: 2020,
                  globals: globals.browser,
                  parserOptions: {
                    project: ["./tsconfig.node.json", "./tsconfig.app.json"],
                    tsconfigRootDir: import.meta.dirname,
                  },
                },
                settings: {
                  react: {
                    version: "detect",
                  },
                },
                plugins: {
                  "react-hooks": reactHooks,
                  "react-refresh": reactRefresh,
                  react: react,
                },
                rules: {
                  ...reactHooks.configs.recommended.rules,
                  "react-refresh/only-export-components": [
                    "warn",
                    { allowConstantExport: true },
                  ],
                  ...react.configs.recommended.rules,
                  ...react.configs["jsx-runtime"].rules,
                },
              },
            )
            .concat(eslintPluginPrettier);
          
    - Edit the eslint scripts in the package.json file: 
        
        .. code-block:: cfg
          :caption: contents of eslint.config.js
          :linenos:
          
          "scripts": {
            ... ,
            "lint": "eslint src --ext ts,tsx --report-unused-disable-directives --max-warnings 0",
            "lint:fix": "eslint src --ext ts,tsx --fix",
          },
          
    - Run ESLint:
        
        .. code-block:: sh
          :linenos:
          
          #npm
          npm run lint
          npm run lint:fix
          #yarn
          yarn lint
          yarn lint:fix
          
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
        
