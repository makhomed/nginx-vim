nginx-vim version 2.0
=====================

syntax/nginx.vim validator

Installation
------------

- ``cd /opt``
- ``git clone https://github.com/makhomed/nginx-vim.git nginx-vim``

Also you need to install ``python3``, ``requests``, ``tar``, ``unzip`` and ``mercurial``.


- yum install python3
- pip3 install requests
- yum install tar
- yum install unzip
- yum install mercurial

Upgrade
-------

- ``cd /opt/nginx-vim``
- ``git pull``

Usage
-----

.. code-block:: none

    usage: nginx-vim [-h] [-q] [-c CONFIG] [--force-sync] [--force-extract]
                     [--check] [--overlapping-check]

    optional arguments:
      -h, --help           show this help message and exit
      -q                   quiet
      -c CONFIG            configuration file (nginx-vim.conf)
      --force-sync         force sync all repositories
      --force-extract      force extract all directives
      --check              run directives check
      --overlapping-check  run directives overlapping check

Script creates ``directives``, ``modules``, ``nginx``, ``nginx.org`` and ``njs`` directories in current working directory.

Automation via cron
-------------------

Configure cron job, for example, in file ``/etc/cron.d/nginx-vim``:

.. code-block:: none

    RANDOM_DELAY=360

    MAILTO=your@email-address

    0 0 * * * root cd /opt/nginx-vim; ./nginx-vim -q --force-sync --force-extract --check

However root permissions not required and script can be runned under unprivileged user, for example:

- # useradd nginx-vim
- # su - nginx-vim
- $ git clone https://github.com/makhomed/nginx-vim.git
- $ crontab -e

.. code-block:: none

    RANDOM_DELAY=360

    MAILTO=your@email-address

    0 0 * * * cd /home/nginx-vim/nginx-vim; ./nginx-vim -q --force-sync --force-extract --check

