# Module `mysql`

## Description

MySQL is a database management system developed & maintained by Oracle. It is mainly used as a RDMS by web applications like Wordpress, Joomla and for smaller applications just in need of a data storage option etc.

## How to use

It is recommended to run only one instance of this module in your project as this is intended as an helper module only.

```bash
sudo docker-compose --env-file run.env up
```

**Before doing that change the password specified in `run.env`!**

### Security

1. It should not provide services which are directly accessible from the interweb but instead it should provide services only to docker containers in your project.
2. The `docker-compose.yml` does not expose any ports.
3. `initdb.d/admin.sql` configures to deny log in requests coming from the interweb to your `root` account in the RDMS. Only requests from hosts containing the string `sqladmin` are allowed. Together with the previous step it only allows requests from docker containers in the same network containing the said string.

#### User per application

**Never use one user for all apps!** For each app a new user should be created.

1. Let `<username>` be the name of the database and the user e.g. `foo`
2. and `<host>` be the name of the complete docker container if you know it already e.g. `foo-bar` or just a part of it e.g. `%foo%` which will also match `foo-bar` (if existing) but also `evilfoo` (if existing). In any way better control what kind of containers have access to the network you are attaching this module to and which names you give them. Docker container names control access but please be aware that docker containers can change their host name. Therefore this provides just very little security and **does not** replace a (very secure machine generated long) password.

Creating a database user for an application can be done like:

1. Log into this module with the `root` account. You can use the module `phpmyadmin` to do that.
2. `CREATE DATABASE <username>`
3. `CREATE USER <username>`
4. `UPDATE mysql.user SET host='<host>' WHERE host='%' AND user='<username>'`
5. `GRANT ALL ON <username>.* TO <username>`
