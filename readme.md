# Docker Odoo

## Install Docker Desktop
https://www.docker.com/products/docker-desktop

## Install Docker Compose
https://docs.docker.com/compose/install/

## Clone Repository
```bash
git clone
```

## Create docker-compose.yml
```bash
version: '3'
services:
  web:
    image: odoo:14.0
    depends_on:
      - db
    ports:
      - "8069:8069"
    volumes:
      - odoo-web-data:/var/lib/odoo
      - ./config:/etc/odoo
    environment:
      - HOST=db
      - USER=odoo
      - PASSWORD=odoo
      - DBNAME=odoo
  db:
    image: postgres:13
    environment:
      - POSTGRES_DB=odoo
      - POSTGRES_USER=odoo
      - POSTGRES_PASSWORD=odoo
    volumes:
      - odoo-db-data:/var/lib/postgresql/data
volumes:
    odoo-web-data:
    odoo-db-data:
    ```
## Run Odoo
```bash
docker-compose up
```

## Access Odoo
http://localhost:8069

## Stop Odoo
```bash
docker-compose down
```

## Restart Odoo
```bash
docker-compose restart
```

## Remove Odoo
```bash
docker-compose down -v
```

## Access Odoo Container
```bash
docker-compose exec web bash
```

## Update Odoo
```bash
docker-compose pull
docker-compose up -d
```

## Backup Odoo
```bash
docker-compose exec db pg_dump -U odoo odoo > backup.sql
```

## Restore Odoo
```bash
docker-compose exec db psql -U odoo odoo < backup.sql
```

## Install Custom Module
```bash
docker-compose exec web odoo -i module_name
```

## Update Custom Module
```bash
docker-compose exec web odoo -u module_name
```

## Uninstall Custom Module
```bash
docker-compose exec web odoo -d db -u module_name
```

## Create Custom Module
```bash
docker-compose exec web odoo scaffold module_name /mnt/extra-addons
```

## Access Postgres
```bash
docker-compose exec db psql -U odoo odoo
```

## Access Odoo Log
```bash
docker-compose logs -f
```

## Access Postgres Log
```bash
docker-compose logs -f db
```

## Access Odoo Configuration
```bash
docker-compose exec web cat /etc/odoo/odoo.conf
```

## Access Postgres Configuration
```bash
docker-compose exec db cat /var/lib/postgresql/data/postgresql.conf
```

## Access Odoo Data
```bash
docker-compose exec web ls /var/lib/odoo
```

## Access Postgres Data
```bash
docker-compose exec db ls /var/lib/postgresql/data
```

## Access Odoo Version
```bash
docker-compose exec web odoo --version
```

## Access Postgres Version
```bash
docker-compose exec db psql --version
```

## Access Odoo Shell
```bash
docker-compose exec web odoo shell
```

## Access Postgres Shell
```bash
docker-compose exec db psql
```

## Access Odoo Database
```bash
docker-compose exec web odoo -d db
```

## Access Postgres Database
```bash
docker-compose exec db psql -d odoo
```

## Access Odoo User
```bash
docker-compose exec web odoo -u odoo
```

## Access Postgres User
```bash
docker-compose exec db psql -U odoo
```

## Access Odoo Password
```bash
docker-compose exec web odoo -p odoo
```

## Access Postgres Password
```bash
docker-compose exec db psql -W odoo
```

## Access Odoo Database Name
```bash
docker-compose exec web odoo -d odoo
```

## Access Postgres Database Name
```bash
docker-compose exec db psql -d odoo
```

## Access Odoo Host
```bash
docker-compose exec web odoo -h db
```

## Access Postgres Host
```bash
docker-compose exec db psql -h localhost
```

## Access Odoo Port
```bash
docker-compose exec web odoo -P 8069
```

## Access Postgres Port
```bash
docker-compose exec db psql -p 5432
```

## Access Odoo Environment
```bash
docker-compose exec web env
```

## Access Postgres Environment
```bash
docker-compose exec db env
```

## Source
```
https://github.com/van-grafity/odoo-16-docker.git
```

## Enable Hyper-V
```bash
Docker Desktop > Settings > General > Use the WSL 2 based engine
or
Open "Control Panel" from the Start menu.
Click on "Programs".
Click on "Turn Windows features on or off".
Check "Hyper-V" and click "OK".
Restart your computer.
```

## \\wsl$ command to work, make sure that your docker desktop is running.
```bash
\\wsl$
```

