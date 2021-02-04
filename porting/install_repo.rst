Install repo 
================

Before installing repo, ensure that you curl and git installed. To install curl & git run the following command :

.. code-block::

    sudo apt install curl && sudo apt install git

Run the following commands to create a .bin directory in the home directory, and include it in your path.
    
.. code-block::

    mkdir -p ~/.bin
    echo export PATH=\$PATH:\$HOME/.bin >> ~/.bashrc
    source ~/.bashrc

Run the following commands to download the repo script and ensure it is executable :

.. code-block::

    curl https://storage.googleapis.com/git-repo-downloads/repo > ~/.bin/repo
    chmod a+rx ~/.bin/repo

