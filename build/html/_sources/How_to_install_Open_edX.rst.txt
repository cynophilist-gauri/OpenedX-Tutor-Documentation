.. _How_to_install_Open_edX:

How to install Open edX?
==============================

Before installing Open edX, you have two decisions to make:

1. Version: 
    * Master is the latest version of the code, newer even than what is running on edx.org.
    * A Release is a version of the code marked and tested for wide use. These are                 named alphabetically for trees: Juniper, Koa, Lilac, etc.

2. Installation Method: 
    * Tutor: (New for Lilac) A community-supported Docker-based environment suited for both production and development.
    * Native: (Deprecated in Lilac, to be removed in Maple) Provides a production-ready installation on an Ubuntu machine of your own, using an Ansible playbook.
    * Devstack: A development environment based on Docker; useful if you want to modify Open edX code locally.
