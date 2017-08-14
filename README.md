# Tutorial-PortablePostGIS

This project is a tutorail and repository of a PostGIS installation without admin rights in a Windows machine with the intention to use the the RiverGis plugin in Qgis.

Preconditios:
* Windows 7 64-bit
* No admin rights
* Qgis 2.18.7

The steps:
1. Select the appropiate packages (architecture, version and so on) and download them
2. install PortgreSQL and test it
3. Intall PostGIS and test it
4. Load a set of data in QGis
5. Load a set of data in RiverGis

## Selecting the appropate packages
Using this source link http://postgis.net/windows_downloads/ I have choosen to install:

* postgresql-9.6.3
* postgis-bundle-pg96-2.3.3
The binaries binaries are at:
* postgresql-9.6.3-3-windows-x64-binaries: 
* postgis-bundle-pg96-2.3.3x64

## Installing PostgreSQL
I have followed this post 
http://www.postgresonline.com/journal/archives/172-Starting-PostgreSQL-in-windows-without-install.html
and this project
https://sourceforge.net/projects/pgsqlportable/

then I have executed some exercices from
https://wiki.postgresql.org/wiki/First_steps
Evrerything fine!

In order to create a cluster, start Postgres and test it I have used the following batch files:
FirstBatch.bat
```
@ECHO ON
REM The script sets environment variables helpful for PostgreSQL
@SET PATH="%~dp0\bin";%PATH%
@SET PGDATA=%~dp0\data
@SET PGDATABASE=postgres
@SET PGUSER=postgres
@SET PGPORT=5439
@SET PGLOCALEDIR=%~dp0\share\locale
"%~dp0\bin\initdb" -U postgres -A trust -E UTF8
"%~dp0\bin\pg_ctl" -D "%~dp0/data" -l logfile start
ECHO "Click enter to stop"
pause
"%~dp0\bin\pg_ctl" -D "%~dp0/data" stop
```
Let's use UTF-8
"(On Windows, however, UTF-8 encoding can be used with any locale.)" (https://www.postgresql.org/docs/9.6/static/multibyte.html#MULTIBYTE-CHARSET-SUPPORTED)

Normalbatch.bat
PsqlShell.bat

## Installing PostgreSQL
Source of instructions:

http://www.bostongis.com/PrinterFriendly.aspx?content_name=postgis_tut01
https://gis.stackexchange.com/questions/41060/how-to-install-postgis-on-windows

```
REM shell interface
"%~dp0bin\psql" -p 5439 -U postgres
```

executing the batch, within the shell type the following comands

```
postgres=#create database geodb;
postgres=#\connect geodb;
geodb=#CREATE EXTENSION postgis;
geodb=#CREATE EXTENSION postgis_topology;
\q
```





