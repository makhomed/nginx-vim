nginx-vim
=========

syntax/nginx.vim validator

Installation
------------

- ``cd /opt``
- ``git clone https://github.com/makhomed/nginx-vim.git nginx-vim``

Also you need to install ``python``, ``pip``, ``requests``, ``tar``, ``unzip`` and Mercurial.

- install python
- install pip https://pip.pypa.io/en/stable/installing/
- pip install requests
- install tar
- install unzip
- install Mercurial

Upgrade
-------

- ``cd /opt/nginx-vim``
- ``git pull``

Usage
-----

.. code-block:: none

    usage: nginx-vim [-h] [-q] [-c CONFIG] [--sync] [--download-all]
                     [--download-last] [--extract] [--check] [--overlapping-check]

    optional arguments:
      -h, --help           show this help message and exit
      -q                   quiet
      -c CONFIG            configuration file (nginx-vim.conf)
      --sync               synchronize with nginx and nginx.org repositories
      --download-all       download all modules
      --download-last      download last module
      --extract            extract all modules
      --check              run directives check
      --overlapping-check  run module directives overlapping check

Script create ``modules``, ``nginx`` and ``nginx.org`` directories in current working directory.

Automation via cron
-------------------

Configure cron job, for example, in file ``/etc/cron.d/nginx-vim``:

.. code-block:: none

    RANDOM_DELAY=360

    MAILTO=your@email-address

    0 0 * * * root cd /opt/nginx-vim; ./nginx-vim -q --sync --download-all --extract --check

