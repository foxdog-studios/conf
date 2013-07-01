conf
====

Prints configuration values from a JSON file to the stdout. Useful within shell
scripts that require values from a configuration file.

conf is licensed under the Apache License, Version 2.0. See $REPO/LICENSE.txt
for more information.

Installation
------------

Install Python 3.x and then from the repository's root run (requires root if
installed globally)

.. code-block:: console

    $ python setup.py install

Usage
-----

Assume we've got the following JSON file, named ``conf.json``, in our working
directory.

.. code-block:: json

    {
        "section": {
            "option": "value"
        }
    }

To print out the value of ``option`` run

.. code-block:: console

    $ conf conf.json section option

Here's a more useful example:

.. code-block:: bash

    function sql
    {
        echo "${@}" | mysql -u "$(conf $CONF db user)" \
                "-p$(conf $CONF db password)" \
                "$(conf $CONF db name)"
    }

    sql 'SELECT * FROM table'
