#################################
Repository Service for TUF Worker
#################################

|Test Docker Image build| |Tests and Lint| |Coverage|

.. |Test Docker Image build| image:: https://github.com/vmware/repository-service-tuf-worker/actions/workflows/test_docker_build.yml/badge.svg
  :target: https://github.com/vmware/repository-service-tuf-worker/actions/workflows/test_docker_build.yml
.. |Tests and Lint| image:: https://github.com/vmware/repository-service-tuf-worker/actions/workflows/ci.yml/badge.svg
  :target: https://github.com/vmware/repository-service-tuf-worker/actions/workflows/ci.yml
.. |Coverage| image:: https://codecov.io/gh/vmware/repository-service-tuf-worker/branch/main/graph/badge.svg
  :target: https://codecov.io/gh/vmware/repository-service-tuf-worker


Repository Service for TUF Worker is part of Repository Service for TUF (RSTUF).

`Repository Service for TUF Repository Worker specific documentation
<https://docs.vmware.com/repository-service-tuf-worker/>`_


Development
###########

Requirements
============

- Python >=3.10
- pip
- Pipenv
- Docker

Getting source code
===================

`Fork <https://docs.github.com/en/get-started/quickstart/fork-a-repo>`_ the
repository on `GitHub <https://github.com/vmware/repository-service-tuf-worker>`_ and
`clone <https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository>`_
it to your local machine:

.. code-block:: console

    git clone git@github.com:YOUR-USERNAME/repository-service-tuf-worker.git

Add a `remote
<https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/configuring-a-remote-for-a-fork>`_ and
regularly `sync <https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/syncing-a-fork>`_ to make sure
you stay up-to-date with our repository:

.. code-block:: console

    git remote add upstream https://github.com/vmware/repository-service-tuf-worker
    git checkout main
    git fetch upstream
    git merge upstream/main


Intalling project requirements
==============================

This repository has the ``requirements.txt`` and the ``requirements-dev.txt``
files to help build your virtual environment.

We also recommend using `Pipenv <https://pipenv.pypa.io/en/latest/>`_ to manage
your virtual environment.

.. code:: shell

  $ pip install pipenv
  $ pipenv shell


Install development requirements


.. code:: shell

  $ pipenv install -d


.. note::

    MacOS running on Macbooks M1

    For developers, after above command, run

    .. code:: shell

        $ pip uninstall cryptography cffi -y
        $ pip cache purge
        $ LDFLAGS=-L$(brew --prefix libffi)/lib CFLAGS=-I$(brew --prefix libffi)/include pip install cffi cryptography


Github Account Token

For the development environment, you will require a Github Account Token to
download Repository Service for TUF REST API container

Access the Github page > Settings > Develop Settings > Personal Access tokens >
Generate new token

This token requires only
``read:packages Download packages from GitHub Package Registry``

Save the token hash

.. note::

    You can also build locally the
    `repository-service-tuf-api <https://github.com/vmware/repository-service-tuf-api>`_
    image and change the `docker-compose.yml` to use the local image.


Runing the API locally

.. code:: shell

  $ make run-dev


See Makefile for more options

Tests
=====

We use `Tox <ttps://tox.wiki/en/latest/>`_ to manage running the tests.

Running tests

.. code:: shell

  $ tox


Managing requirements
=====================

Installing new requirements
---------------------------

Project requirements

.. code:: shell

  $ pipenv install {package}


Development requirements

.. code:: shell

  $ pipenv install -d {package}


Updating requirements files from Pipenv
---------------------------------------

.. code:: shell

  $ make requirements
