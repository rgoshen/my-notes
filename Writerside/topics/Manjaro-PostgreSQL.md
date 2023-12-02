# Manjaro PostgreSQL

[![manajaro-logo](manjaro_logo.png)](https://manjaro.org/)

## Install PostgreSQL {collapsible="true" default-state="expanded"}

1. Install

```bash
sudo pacman -S yay     # if not already installed
yay postgresql pgadmin4
```

1. Setup posgresql service

```bash
sudo -u postgres -i     # login as postgres
initdb --locale $LANG -E UTF8 -D '/var/lib/postgres/data/'
sudo systemctl enable --now postgresql
sudo systemctl status PostgreSQL    # check for any errors
```

2. Setup password

```bash
psql -U postgres
postgres = # \password    # to set password
```

3. Setup connection security

```bash
su
cd /var/lib/postgres/data
cp pg_hba.conf pg_hba.conf.backup
nano pg_hba.conf
```

## Seed a Database {collapsible="true" default-state="expanded"}

- login as postgres

```bash
sudo -u postgres -i
```

- cd to working/project directory

```bash
cd [folder]
```

- seed database

```bash
psql < filename.sql
```

<seealso>
[User Guide](https://mirrors.gigenet.com/OSDN//storage/g/m/ma/manjaro/Manjaro-User-Guide.pdf) |
[Manjaro Forum](https://forum.manjaro.org/) |
[Manjaro Wiki](https://wiki.manjaro.org/index.php/Main_Page) |
[How to setup PostgreSQL and PGAdmin on Manjaro Linux / Arch](https://dev.to/tusharsadhwani/how-to-setup-postgresql-on-manjaro-linux-arch-412l) |
[Arch Linux PostgreSQL Wiki](https://wiki.archlinux.org/title/PostgreSQL)
</seealso>
