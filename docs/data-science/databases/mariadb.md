# MariaDB

## Description

- Open source relational database management system (RDBMS);
- Fork of **MySQL**;
- Developed by the original MySQL developers;
- Written in C, C++, Bash.

## Installation

### Docker

```bash
docker run --name <your-container-name> -e MYSQL_ROOT_PASSWORD=<your-mariadb-root-password> -v <local-directory-absolute-path>:/docker-entrypoint-initdb.d/ -p 3306:3306 -d mariadb
```

This command will **download the latest mariadb image** from Docker Hub if you
don't have it locally, and **initialize container's MariaDB**.

Note: `-v <local-directory-absolute-path>:/docker-entrypoint-initdb.d/` is for
**initializing container's mariadb with a `.sql` file**. You can mount a local
directory containing `.sql` files. The `.sql` files will be **executed in**
**alphabetical order when the container starts**. A common practice is to `cd`
into the local directory containing the `.sql` files and type `-v`
`$PWD:/docker-entrypoint-initdb.d/` instead of typing the absolute path.
