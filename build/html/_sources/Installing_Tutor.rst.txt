.. _Installing_Tutor:

Installing Tutor
=================

Requirements
---------------

* Supported OS: Tutor runs on any 64-bit, UNIX-based OS. It was also reported to work on Windows (with `WSL 2 <Supported OS: Tutor runs on any 64-bit, UNIX-based OS. It was also reported to work on Windows (with WSL 2).>`_).
* Required software:
    * `Docker <https://docs.docker.com/engine/installation/>`_: v18.06.0+
    * `Docker Compose <https://docs.docker.com/compose/install/>`_: v1.22.0+

.. warning::
    Do not attempt to simply run ``apt-get install docker docker-compose`` on older Ubuntu platforms, such as 16.04 (Xenial), as you will get older versions of these utilities.

    * Ports 80 and 443 should be open. If other web services run on these ports, check the tutorial on `how to setup a web proxy <https://docs.tutor.overhang.io/tutorials/proxy.html#web-proxy>`_.
    * Hardware:
        * Minimum configuration: 4 GB RAM, 2 CPU, 8 GB disk space
        * Recommended configuration: 8 GB RAM, 4 CPU, 25 GB disk space

.. note::
    On Mac OS, by default, containers are allocated 2 GB of RAM, which is not enough. You should follow `these instructions from the official Docker documentation <https://docs.docker.com/docker-for-mac/#advanced>`_ to allocate at least 4-5 GB to the Docker daemon. If the deployment fails because of insufficient memory during database migrations, check the `relevant section in the troubleshooting guide. <https://docs.tutor.overhang.io/troubleshooting.html#migrations-killed>`_

Download
-----------

    Choose **one** of the installation methods below. If you install Tutor in different ways, you will end up with multiple tutor executables, which is going to be very confusing. At any time, you can check the path to your tutor executable by running which tutor.

    1. Python package

        Requirements:
        Check the “tutor” package on Pypi: https://pypi.org/project/tutor. You will need Python >= 3.6 with pip and the libyaml development headers. On Ubuntu, these requirements can be installed by running:
        
        ``sudo apt install python3 python3-pip libyaml-dev``
        
        If all the conditions are met, execute the following command:
        
        ``pip install "tutor[full]"``

        The following happens in the backend when this command is executed:

        1. ``pip``, the package installer for Python, is executed to download and install Tutor and all its dependencies from the Python Package Index (PyPI).
        2. The ``tutor[full]`` specification tells ``pip`` to install the full version of Tutor, which includes all optional dependencies for features such as advanced analytics, content rendering, and interactive exercises.
        3. During the installation process, ``pip`` creates a virtual environment, a self-contained Python environment that is isolated from the system's global Python installation.
        4. Once the virtual environment is set up, ``p\ip`` installs all required packages for Tutor, including its core modules and dependencies, such as Django, PostgreSQL, and Redis.
        5. Finally, the tutor command-line interface (CLI) is installed, which allows you to create and manage Tutor instances and courses.

    2. Binary release

        The latest binaries can be downloaded from https://github.com/overhangio/tutor/releases. From the command line:

        ``sudo curl -L "https://github.com/overhangio/tutor/releases/download/v15.3.5/tutor-$(uname -s)_$(uname -m)" -o /usr/local/bin/tutor sudo chmod 0755 /usr/local/bin/tutor``

        This is the simplest and recommended installation method for most people who do not have Python 3 on their machine. Note however that **you will not be able to use custom plugins** with this pre-compiled binary. The only plugins you can use with this approach are those that are already bundled with the binary: see the `existing plugins <https://docs.tutor.overhang.io/plugins/intro.html#existing-plugins>`_.

    3. Installing from source

        To inspect the Tutor source code, install Tutor from `the Github repository <https://github.com/overhangio/tutor>`_:

        ``git clone https://github.com/overhangio/tutor``
        ``cd tutor``
        ``pip install -e .``

Configuring DNS records
========================

When running a server in production, it is necessary to define `DNS records <https://en.wikipedia.org/wiki/Domain_Name_System#Resource_records>`_ which will make it possible to access your Open edX platform by name in your browser. The precise procedure to create DNS records varies from one provider to the next and is beyond the scope of these docs. You should create a record of type A with a name equal to your LMS hostname (given by ``tutor config printvalue LMS_HOST``) and a value that indicates the IP address of your server. Applications other than the LMS, such as the studio, ecommerce, etc. typically reside in subdomains of the LMS. Thus, you should also create a CNAME record to point all subdomains of the LMS to the LMS_HOST.