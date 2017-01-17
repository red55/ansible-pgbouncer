pgbouncer
=========

This role configures PgBouncer PostgreSQL connection mux utility.

Example minimal data requirements
---------------------------------

    pgbouncer_users:
      - name: username
        pass: unencrypted_password

    pgbouncer_databases:
      - name: databasename
        host: hostname

Debugging
---------

If pgbouncer fails to start:-

    sudo -u postgres pgbouncer -d /etc/pgbouncer/pgbouncer.ini -vvvv

Testing a connection to a remote database

    psql -h localhost -p 6432 -U username databasename


License
-------

LGPL

Author Information
------------------

- Alexey Medvedchikov, 2GIS, LLC

