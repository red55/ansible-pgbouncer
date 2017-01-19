pgbouncer
=========

This role configures PgBouncer PostgreSQL connection mux utility.

Example minimal data requirements
---------------------------------

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

