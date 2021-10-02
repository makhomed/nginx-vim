nginx-vim
=========

syntax/nginx.vim validator

Installation
------------

- ``cd /opt``
- ``git clone https://github.com/makhomed/nginx-vim.git nginx-vim``

Also you need to install ``python``, ``pip``, ``requests``, ``tar``, ``unzip`` and Mercurial.


- yum install python3
- pip3 install requests
- yum install tar
- yum install unzip
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
      --overlapping-check  run directives overlapping check

Script creates ``modules``, ``nginx`` and ``nginx.org`` directories in current working directory.

Automation via cron
-------------------

Configure cron job, for example, in file ``/etc/cron.d/nginx-vim``:

.. code-block:: none

    RANDOM_DELAY=360

    MAILTO=your@email-address

    0 0 * * * root cd /opt/nginx-vim; ./nginx-vim -q --sync --download-all --extract --check

However root permissions not required and script can be runned under unprivileged user, for example:

- # useradd nginx-vim
- # su - nginx-vim
- $ git clone https://github.com/makhomed/nginx-vim.git
- $ crontab -e

.. code-block:: none

    RANDOM_DELAY=360

    MAILTO=your@email-address

    0 0 * * * cd /home/nginx-vim/nginx-vim; ./nginx-vim -q --sync --download-all --extract --check

