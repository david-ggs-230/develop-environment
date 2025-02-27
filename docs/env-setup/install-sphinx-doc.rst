.. _install-sphinx-doc:

.. rst-class:: title-center h1
   
##################################################################################################
Sphinx Doc Environment
##################################################################################################

**************************************************************************************************
Install Python
**************************************************************************************************

Install Python following the instructions in: :ref:`install-python`.

Quick guide:
    
    - Go to the official Python download page and choose the version suitable for your system.
    - Run the installer by double-clicking it and follow the on-screen prompts. Be sure to check the "Add Python to PATH" option, which will automatically update your PATH environment variable.
    - Click "Install Now" for a standard installation, or choose "Customize installation" if you'd like to modify settings such as the installation location and advanced options.
    - To verify Python installation, run the following commands:
      
      .. code-block:: sh
        :linenos:
        
        # verify Python installation
        python --version
        python -V
        

**************************************************************************************************
Create Sphinx-Doc Project
**************************************************************************************************

#. Create the Sphinx-Doc folder <doc>.
#. Navigate to the <doc> folder.
#. Create and Activate Python virtual environment
    
    .. code-block:: sh
        :linenos:
        
        python -m venv .venv
        # Activate the Python virtual environment - Windows
        .venv\Scripts\activate.bat
        
#. Install Sphinx-Doc packages.
    
    .. code-block:: sh
        :linenos:
        
        # Installing py packages
        pip install -i https://pypi.tuna.tsinghua.edu.cn/simple -U sphinx sphinx_rtd_theme myst-parser sphinx-autobuild sphinx-design
        
    
**************************************************************************************************
Sphinx-Doc Initialization
**************************************************************************************************

#. Run sphinx-quickstart <doc-folder>
#. Generate html build
#. Run command: 
    
    .. code-block:: sh
        :linenos:
        
        # interactive
        sphinx-quickstart docs
        # Non-interactive
        sphinx-quickstart --sep --project="<project-name>" --author="<author-name>" -v "<version>" --quiet docs 
        # run html build: 
        #    1. sphinx-build -M html docs/source/ docs/build/
        #       # OR
        #    2. cd docs && make clean && make html
        cd docs
        make clean && make html
        
    
**************************************************************************************************
Sphinx-Doc Configuration
**************************************************************************************************

#. Modify the conf.py file
    
    .. code-block:: cfg
        :caption: contents of the conf.py file
        :linenos:
        
        # -*- coding: utf-8 -*-
        
        # Configuration file for the Sphinx documentation builder.
        #
        # For the full list of built-in configuration values, see the documentation:
        # https://www.sphinx-doc.org/en/master/usage/configuration.html
        
        # -- Project information -----------------------------------------------------
        # https://www.sphinx-doc.org/en/master/usage/configuration.html#project-information
        
        import sphinx_rtd_theme
        
        project = 'Sphinx Documentation'
        copyright = '2025, David G.'
        author = 'David G.'
        release = '1.0.0'
        
        # -- General configuration ---------------------------------------------------
        # https://www.sphinx-doc.org/en/master/usage/configuration.html#general-configuration
        
        #extensions = []
        extensions = [
                'myst_parser',
                'sphinx_rtd_theme',
                "sphinx_design"
            ]
        
        templates_path = ['_templates']
        exclude_patterns = []
        myst_enable_extensions = ["colon_fence"]
        numfig = True
        
        # -- Options for HTML output -------------------------------------------------
        # https://www.sphinx-doc.org/en/master/usage/configuration.html#options-for-html-output
        
        #html_theme = 'alabaster'
        #html_static_path = ['_static']
        
        html_theme = "sphinx_rtd_theme"
        #html_theme_path = [sphinx_rtd_theme.get_html_theme_path()]
        #html_theme_path = ["."]
        html_static_path = ['_static']
        html_show_sourcelink = False
        html_css_files = [
            'css/custom-theme.css' 
            # 'css/bootstrap.min.css'
        ]
        html_js_files = [
            # 'css/bootstrap.min.js'
        ]
        html_theme_options = {
            # 'analytics_id': 'G-XXXXXXXXXX',  #  Provided by Google in your dashboard
            # 'analytics_anonymize_ip': False,
            
            
            'logo_only': False,
            #'display_version': True,
            'prev_next_buttons_location': 'bottom',
            'style_external_links': True,
            'vcs_pageview_mode': '',
            #'style_nav_header_background': 'white',
            # Toc options
            'collapse_navigation': True,
            'sticky_navigation': True,
            'navigation_depth': 6,
            'includehidden': True,
            'titles_only': False
        }
        
        html_context = {
            'display_github': False
        }
        
#. Create custom-theme.css file
    
    .. code-block:: cfg
        :caption: contents of the _static/css/custom-theme.css file
        :linenos:
        
        /*.wy-breadcrumbs>li.wy-breadcrumbs-aside {
            display: none;
        }*/
        
        .wy-nav-content {
           max-width: 90%;
           background: #fcfcfc;
        }
        .wy-nav-content-wrap {
           background: #fcfcfc;
        }
        .rst-content {
            background-color: transparent;
        }
        .title-center h1 {
            font-size: 250%; 
            margin-top: 0;
            font-weight: 700;
            font-family: Roboto Slab,ff-tisa-web-pro,Georgia,Arial,sans-serif;
            text-align: center;
        }
        
        p.title-center.h2 {
            font-size: 200%;  
            margin-top: 0;
            text-align: center;
            font-weight: 700;
            font-family: Roboto Slab,ff-tisa-web-pro,Georgia,Arial,sans-serif;
        }
        
        p.title-center.h1 {
            font-size: 250%; 
            margin-top: 0;
            font-weight: 700;
            font-family: Roboto Slab,ff-tisa-web-pro,Georgia,Arial,sans-serif;
            text-align: center;
        }
        
        p.title-center.h6 {
            font-size: 100%;  
            margin-top: 0;
            text-align: center;
            font-weight: 700;
            font-family: Roboto Slab,ff-tisa-web-pro,Georgia,Arial,sans-serif;
        }
        
        
        p.title-left.h2 {
            font-size: 200%;  
            margin-top: 0;
            text-align: left;
            font-weight: 700;
            font-family: Roboto Slab,ff-tisa-web-pro,Georgia,Arial,sans-serif;
        }
        
        p.title-left.h1 {
            font-size: 250%; 
            margin-top: 0;
            font-weight: 700;
            font-family: Roboto Slab,ff-tisa-web-pro,Georgia,Arial,sans-serif;
            text-align: left;
        }
        
        p.title-left.h3 {
            font-size: 150%;  
            margin-top: 0;
            text-align: left;
            font-weight: 700;
            font-family: Roboto Slab,ff-tisa-web-pro,Georgia,Arial,sans-serif;
        }
        
        
        p.title-left.h4 {
            font-size: 125%;  
            margin-top: 0;
            text-align: left;
            font-weight: 700;
            font-family: Roboto Slab,ff-tisa-web-pro,Georgia,Arial,sans-serif;
        }
        
        
        .rst-content div.code-block-caption {
            text-align: left;
        }
        
        img.sd-svg-primary { filter: invert(.5) sepia(0.5) saturate(80) hue-rotate(208deg); }
        
        span.sd-text-decoration-line-underline {
            text-decoration-line: underline;
        }
        

**************************************************************************************************
Document Structures
**************************************************************************************************

#. ``###########`` with overline, for parts
#. ``***********`` with overline, for chapters
#. ``===========`` for sections
#. ``-----------`` for subsections
#. ``^^^^^^^^^^^`` for subsubsections
#. ``"""""""""""`` for paragraphs

**************************************************************************************************
Build Command
**************************************************************************************************
    
    .. code-block:: sh
        :linenos:
        
        # Activate .venv
        .venv\Scripts\activate
        # navigate to docs folder
        cd docs
        # clean
        make clean
        # build html
        make html
        # clean and build
        make clean && make html
        