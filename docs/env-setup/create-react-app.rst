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
          