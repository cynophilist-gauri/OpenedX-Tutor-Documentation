.. _How_does_Tutor_simplify_Open_edX_deployment:

How does Tutor simplify Open edX deployment?
=============================================

Tutor simplifies the deployment of Open edX by:

1. Separating the configuration logic from the deployment platforms.
2. Running application processes in cleanly separated `docker containers <https://www.docker.com/resources/what-container>`_.
3. Providing user-friendly, reliable commands for common administration tasks, including upgrades and monitoring.
4. Using a simple `plugin system <https://docs.tutor.overhang.io/plugins/intro.html#plugins>`_ that makes it easy to extend and customise Open edX.

.. image:: tutor.png
    :alt: open edX + docker = Tutor
    :align: center
    :width: 40%

Because Docker containers are becoming an industry-wide standard, that means that with Tutor it becomes possible to run Open edX anywhere: for now, Tutor supports deploying on a local server, with `docker-compose <https://docs.docker.com/compose/overview/>`_, and in a large cluster, with Kubernetes. But in the future, Tutor may support other deployment platforms.


Features
===========

* 100% `open source <https://github.com/overhangio/tutor>`_
* Runs entirely on Docker
* World-famous 1-click `installation and upgrades <https://docs.tutor.overhang.io/install.html>`_
* Comes with batteries included: `theming, SCORM, HTTPS, web-based administration interface, mobile app, custom translations, etc. <https://github.com/overhangio/indigo>`_
* Extensible architecture with `plugins <https://docs.tutor.overhang.io/plugins/index.html>`_
* Works with `Kubernetes <https://docs.tutor.overhang.io/k8s.html>`_
* Amazing premium plugins available in the `Tutor Wizard Edition <https://overhang.io/tutor/wizardedition>`_, including `Cairn <https://overhang.io/tutor/plugin/cairn>`_ the next-generation analytics solution for Open edX.
* No technical skill required with the `zero-click Tutor AWS image <https://docs.tutor.overhang.io/install.html#zero-click-aws-installation>`_