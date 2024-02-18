# Basic CLI Commands

## Linux Flavors {collapsible="true" default-state="expanded"}

- [Manjaro](Manjaro-Linux-Overview.md)

## Basic Commands {collapsible="true" default-state="expanded"}

### Change Owner

```bash
sudo chown -R [username] /[path to file or folder]
```

`-R`: recursive

### Change Permissions

```bash
sudo chmod -R ugo+rwx /[path to file or folder]
```

`-R`: recursive

u = user g = group o = other

r = read w = write x = execute

## PostgreSQL Commands {collapsible="true" default-state="expanded"}

- check postgreSQL service status

```bash
sudo service postgresql status
```

- start postgreSQL service

```bash
sudo service postgresql start
```

- stop postgreSQL service

```bash
sudo service postgresql stop
```

- run postgreSQL

```bash
sudo service postgresql start
sudo -u postgres psql
```

- seed a database (make sure you are in the project directory)

```bash
psql < filename.sql
```

<seealso>
    <!--Provide links to related how-to guides, overviews, and tutorials.-->
</seealso>