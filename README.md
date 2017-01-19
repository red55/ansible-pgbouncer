pgbouncer
=========

This role configures PgBouncer PostgreSQL connection mux utility.

Postgres server performance degrades when handling a high number of connection due to a 1:1 mapping of connection to Postgres backend processes. PgBouncer is a threaded pooler which can reduce the number of backend processes and the handshaking involved in setting up a new connection.

Example minimal data requirements
---------------------------------

Ansible handles the templating of userlist.txt, including the md5 hashing.

    pgbouncer_users:
      - name: username
        pass: unencrypted_password
      - name: postgres
        host: unencrypted_password

Debugging
---------

If pgbouncer fails to start:-

    sudo -u postgres pgbouncer -d /etc/pgbouncer/pgbouncer.ini -vvvv

Testing a connection to a remote database

    psql -h localhost -p 6432 -U username databasename

Stats
-----

The default 1.7.2 configuration provides peer authentication of the pgbouncer database to show stats.
NOTE: this still requires a userlist.txt entry for the postgres user.

    sudo -u postgres psql -p 6432 pgbouncer -c 'show pool;'

    sudo -u postgres psql -p 6432 pgbouncer -c 'show stats;'


Reloading / restarting
----------------------

Key config changes such as pool sizing do not require a full restart

sudo /etc/init.d/pgbouncer reload


License
-------

LGPL

Author Information
------------------

- Alexey Medvedchikov, 2GIS, LLC

