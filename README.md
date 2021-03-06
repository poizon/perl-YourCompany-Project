# YourCompany Project in Perl [![Build Status](https://travis-ci.org/akzhan/perl-YourCompany-Project.png?branch=master)](https://travis-ci.org/akzhan/perl-YourCompany-Project)

Modern Web project in Perl using [Mojolicious](http://mojolicious.org/) and [DBIx::Class](http://search.cpan.org/~ribasushi/DBIx-Class).

"/api" route also provides implementation of [OpenAPI](https://www.openapis.org/) protocol.

Some configuration settings like database ones embedded to reduce the learning curve.

## Installation

Requirements:

 *  Perl 5.20+
 *  `cpanm`

```bash
cpanm --installdeps .

# for development purposes
cpanm --installdeps --with-develop .
```

## Database

Note that our boilerplate depends on Postgres 9.5+.

You should create user and database.

```
psql postgres
postgres => CREATE USER yourself PASSWORD 'protected';
postgres => CREATE DATABASE yourdatabase OWNER=yourself ENCODING=utf8;
postgres => \q
```

and, as usually, do "[sqitch](http://sqitch.org/) deploy".

By default, Sqitch will read sqitch.conf in the current directory for settings. But it will also read ~/.sqitch/sqitch.conf for user-specific settings. Get it from git and setup.

```bash
sqitch config --user user.name 'user_login'
sqitch config --user user.email 'email@example.com'
```

## Configuration

Usually You need to override *config/defaults.yml* with *config/local.yml* and exclude latest from VCS tracking.

## Usage

### Run

```bash
bin/http # to run HTTP server
bin/cli routes # mojo cli
```

### Unit tests

```bash
prove t -r
```

### Critique

```bash
bin/plint lib
```

### REPL

```bash
bin/re.pl
```

### psql

```bash
bin/psql
```

### pgcli

Install [pgcli](http://pgcli.com).

```bash
bin/pgcli
```

## Swagger UI

YourCompany Project supports [OpenAPI](https://www.openapis.org/) and allows to visualize and interact with the API’s resources
through [Swagger UI](http://swagger.io/swagger-ui/).

Simply do

```bash
git submodule update --init
bin/http
```

and open [its swagger page](http://localhost:7777/swagger-ui/dist/index.html).

## CREDITS

 * Database plan to [Max Travinichev](mailto:uatrigger@gmail.com) [@travinichev](https://github.com/travinichev).
 * Mojolicious application to [Vladimir Melnichenko](mailto:melnichenkovv@gmail.com).
 * find or throw pattern to Eugen Konkov [@KES777](https://github.com/KES777).
