# PostgreSQL

[![postgresql](postgresql.png)](https://www.postgresql.org/)

## Basic Commands

### cli

- create database

```bash
createdb [database-name]
```

- open database

```bash
psql [database-name]
```

- seed database

```bash
psql < file-name.sql
```

- drop database

```bash
dropdb [database-name]
```

### psql

- list all databases

```bash
/l
```

- connect to specific database

```bash
/c [db_name]
```

- list all tables in current database

```bash
/dt
```

- get details about a specific table

```bash
/d [table_name]
```

- quit psql

```bash
/q
```

<seealso>
[![Postgres](https://img.shields.io/badge/Docs-postgres-%23316192.svg?style=flat&logo=postgresql&logoColor=white)](https://www.postgresql.org/docs/)
</seealso>
