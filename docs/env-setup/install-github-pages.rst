.. _install-github-pages:

.. rst-class:: title-center h1
   
##################################################################################################
Hosting Sphinx Doc on GitHub Pages
##################################################################################################

Reference: `Deploy Sphinx documentation to GitHub Pages (https://coderefinery.github.io/documentation/gh_workflow/) <https://coderefinery.github.io/documentation/gh_workflow/>`_ 

To host your docs on GitHub Pages, we need to enable GitHub Pages for our repo. To do that, we need to create a branch that only contains html files. We’ll name this branch gh-pages, as GitHub looks for this name and automatically starts hosting your documentation on pages.

**************************************************************************************************
Creating a github repo
**************************************************************************************************

- Click on ``Create a repository``
- Goto branch ``main``
- Create the documentation source folder ``docs/``
- Create a ``gh-pages`` branch

**************************************************************************************************
Add the GitHub Action to the new Git repository
**************************************************************************************************

- Goto a github repo
- Goto branch ``main``
- Create an empty file .nojekyll
- Add a new file at .github/workflows/documentation.yaml, containing:
    
    .. code-block:: cfg
      :caption: contents of the ``.github/workflows/documentation.yaml`` file 
      :linenos:
      
      name: Publish Sphinx Documentation
      
      on: [push, pull_request, workflow_dispatch]
      
      permissions:
        contents: write
      
      jobs:
        publish_sphinx_docs:
          runs-on: ubuntu-latest
          permissions:
            contents: write
          steps:
            - uses: actions/checkout@v4
            - uses: actions/setup-python@v5
              with:
                python-version: '3.12' 
            - name: Install dependencies
              run: |
                pip install sphinx sphinx_rtd_theme myst_parser sphinx-autobuild sphinx-design
            - name: Sphinx build
              run: |
                sphinx-build docs _build
            - name: Deploy to GitHub Pages
              uses: peaceiris/actions-gh-pages@v3
              if: ${{ github.event_name == 'push' && github.ref == 'refs/heads/main' }}
              with:
                publish_branch: gh-pages
                github_token: ${{ secrets.GITHUB_TOKEN }}
                publish_dir: _build/
                force_orphan: true
                
- Navigate to the ``Actions`` tab
    
    - Under ``All workflows``
    - Check ``documentation`` workflow is running
    - Click to see the running details
    
**************************************************************************************************
Enable GitHub Pages
**************************************************************************************************

- On GitHub go to ``Settings`` -> ``Pages``.
- In the ``Source`` section, choose ``Deploy from a branch`` in the dropdown menu.
- In the ``Branch`` section choose ``gh-pages`` and ``/root`` in the dropdown menus and click save.
- Verify the pages deployment in the Actions list.
    
**************************************************************************************************
Verify the result
**************************************************************************************************

Github pages should now be live on ``https://USER.github.io/<repo-name>/`` (replace USER).
    
**************************************************************************************************
Verify refreshing the documentation
**************************************************************************************************

- Commit some changes to the documentation
- Verify that the documentation website refreshes after changes (can take few seconds or a minute)

