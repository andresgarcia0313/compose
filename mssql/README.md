## Compose sample : MS SQL server database

Project structure:

```
.
└── compose.yaml
```

[*compose.yaml*](compose.yaml)

```
services:

  db:
    image: mcr.microsoft.com/mssql/server:version
    ...
```

The compose file defines an application with service `db`. 

When deploying, docker compose maps the container port 1433 to port 1433 of the host as specified in the file.
Make sure port 1433 on the host is not being used by another container, otherwise the port should be changed.


## Deploy with docker compose

```
$ docker compose up -d
Creating network "mssql_default" with the default driver
a9dca2f6722a: Pull complete
Digest: sha256:9b700672670bb3db4b212e8aef841ca79eb2fce7d5975a5ce35b7129a9b90ec0
Status: Downloaded newer image for microsoft/mssql-server-linux:latest
Creating mssql ... done
```

## Expected result

Listing containers must show two containers running and the port mapping as below:

```
$ docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                  NAMES
7f3a2a7ea5c0        microsoft/mssql-server-linux   "/opt/mssql/bin/sqls…"   4 minutes ago       Up 4 minutes        0.0.0.0:1433->1433/tcp             mssql
```

After the application starts, connect to `http://localhost:1433` in your client db.

Stop and remove the containers

```
$ docker compose down
```
docker compose down;docker compose build;docker compose up -d