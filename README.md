PostgreSQL 9.3 plugin for Dokku
---------------------------

Project: https://github.com/progrium/dokku


Installation
------------
```
cd /var/lib/dokku/plugins
git clone https://github.com/asaushkin/dokku-postgresql-plugin postgresql
dokku plugins-install
```


Commands
--------
```
$ dokku help
    postgresql:activity                             Show current processes in the postgresql instance
    postgresql:bash                                 Enter into bash on the PostgreSQL docker container 
    postgresql:create <app>                         Create a Postgresql database
    postgresql:dblist                               List all databases
    postgresql:dbsize                               Size all databases
    postgresql:delete <app>                         Delete specified Postgresql database
    postgresql:kill <id>                            Terminate a backend process
    postgresql:psql <app>                           Launch a postgresql console for a given app or as admin user (without appname)
    postgresql:start                                Start the Postgresql docker container if it isn't running
    postgresql:status                               Shows status of Postgresql
    postgresql:stop                                 Stop the Postgresql docker container
    postgresql:tsize <app>                          Size all user tables in database <app>
    postgresql:url <app>                            Show an application DATABASE_URL
```

Usage
------------

Start PostgreSQL:
```
$ dokku postgresql:start                 # Server side
..or..
$ ssh dokku@server postgresql:start      # Client side

Example Output:

9f3d9d19248c110fce9f8489482adafd2172834a0f1d2db9f0140141927501b9
```

Create a new DB (app with same name has to exist):
```
$ dokku postgresql:create foo            # Server side
..or..
$ ssh dokku@server postgresql:create foo # Client side

Example Output:

CREATE ROLE
CREATE DATABASE
GRANT
-----> Creating /home/dokku/foo/ENV
-----> Setting config vars and restarting foo
DATABASE_URL: postgres://foo:ultrastrongpassword@172.17.0.28:5432/foo
-----> Releasing foo ...
-----> Release complete!
-----> Deploying foo ...
-----> Deploy complete!
```

Authors
------------

* Andrew G. Saushkin <asaushkin@gmail.com>
* Jeffery Utter (origin: https://github.com/jeffutter/dokku-postgresql-plugin)


