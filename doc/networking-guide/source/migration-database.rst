.. _migration-database:

========
Database
========

The upgrade of the Networking service database is implemented with Alembic
migration chains. The migrations in the ``alembic/versions`` contain the
changes needed to migrate from older Networking service releases to newer ones.

Since Liberty, Networking maintains two parallel Alembic migration branches.

The first branch is called expand and is used to store expansion-only
migration rules. These rules are strictly additive and can be applied while the
Neutron server is running.

The second branch is called contract and is used to store those migration
rules that are not safe to apply while Neutron server is running.

The intent of separate branches is to allow invoking those safe migrations
from the expand branch while the Neutron server is running and therefore
reducing downtime needed to upgrade the service.

A database management command-line tool uses the Alembic library to manage the
migration.

Database management command-line tool
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The database management command-line tool is called
:command:`neutron-db-manage`. Pass the :option:`--help` option to the tool for
usage information.

The tool takes some options followed by some commands:

.. code-block:: console

   $ neutron-db-manage <options> <commands>

The tool needs to access the database connection string, which is provided in
the ``neutron.conf`` configuration file in an installation. The tool
automatically reads from ``/etc/neutron/neutron.conf`` if it is present.
If the configuration is in a different location, use the following command:

.. code-block:: console

   $ neutron-db-manage --config-file /path/to/neutron.conf <commands>

Multiple :option:`--config-file` options can be passed if needed.

Instead of reading the DB connection from the configuration file(s), you can
use the :option:`--database-connection` option:

.. code-block:: console

   $ neutron-db-manage --database-connection
     mysql+pymysql://root:secret@127.0.0.1/neutron?charset=utf8 <commands>

The `branches`, `current`, and `history` commands all accept a
:option:`--verbose` option, which, when passed, will instruct
:command:`neutron-db-manage` to display more verbose output for the specified
command:

.. code-block:: console

   $ neutron-db-manage current --verbose

.. note::

   The tool usage examples below do not show the options. It is assumed that
   you use the options that you need for your environment.

In new deployments, you start with an empty database and then upgrade to
the latest database version using the following command:

.. code-block:: console

   $ neutron-db-manage upgrade heads

After installing a new version of the Neutron server, upgrade the database
using the following command:

.. code-block:: console

   $ neutron-db-manage upgrade heads

In existing deployments, check the current database version using the
following command:

.. code-block:: console

   $ neutron-db-manage current

To apply the expansion migration rules, use the following command:

.. code-block:: console

   $ neutron-db-manage upgrade --expand

To apply the non-expansive migration rules, use the following command:

.. code-block:: console

   $ neutron-db-manage upgrade --contract

To check if any contract migrations are pending and therefore if offline
migration is required, use the following command:

.. code-block:: console

   $ neutron-db-manage has_offline_migrations

.. note::

   Offline migration requires all Neutron server instances in the cluster to
   be shutdown before you apply any contract scripts.

To generate a script of the command instead of operating immediately on the
database, use the following command:

.. code-block:: console

   $ neutron-db-manage upgrade heads --sql

   .. note::

      The `--sql` option causes the command to generate a script.  The script
      can be run later (online or offline), perhaps after verifying and/or
      modifying it.

To migrate between specific migration versions, use the following command:

.. code-block:: console

   $ neutron-db-manage upgrade <start version>:<end version>

To upgrade the database incrementally, use the following command:

.. code-block:: console

   $ neutron-db-manage upgrade --delta <# of revs>

.. note::

   Database downgrade is not supported.
