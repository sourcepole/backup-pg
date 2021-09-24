Postgres DB backup
==================

Purpose
-------

Dump all DBs in a cluster to a directory.

Usage
-----

(taken from `dump_postgres_dbs --help`)

```
usage: dump_postgres_dbs [--ignore-not-accepting-connections] [--ignore-does-not-exist] [/path/to/backup/dir]
       dump_postgres_dbs --help

    --ignore-not-accepting-connections

         Ignore pg_dump errors resulting from DBs that do not
         allow to be connected to.

    --ignore-does-not-exist

         Ignore pg_dump errors resulting from DBs that do not
         exist.

    /path/to/backup/dir

         Directory where `pg_dump`s of DBs will be saved.
         Default is /var/lib/postgresql/backup
```

How to release a new version of this package
--------------------------------------------

```
apt-get install dpkg-dev devscripts
debchange --distribution unstable --no-auto-nmu --maintmaint --increment "see git log"  && \
dpkg-buildpackage -b -tc -rfakeroot                                                     && \
rm ../backup-pg_*_*.changes                                                             && \
rm ../backup-pg_*_*.buildinfo                                                           && \
mv ../backup-pg_*_all.deb .                                                             && \
git add    backup-pg_*_all.deb                                                          && \
git commit backup-pg_*_all.deb debian/changelog -m "build new package"
```

Authorship
----------

`dump_postgres_dbs` started its life as http://forritan.blogspot.ch/2012/10/postgresql-backup-script.html,
was later improved by Pirmin Kalberer and then by Tomáš Pospíšek
