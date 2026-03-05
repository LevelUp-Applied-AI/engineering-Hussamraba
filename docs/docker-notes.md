# Docker Notes — Day 9

## Docker Version
[Client:
 Version:           28.2.2
 API version:       1.50
 Go version:        go1.23.1
 Git commit:        28.2.2-0ubuntu1~24.04.1
 Built:             Wed Sep 10 14:16:39 2025
 OS/Arch:           linux/amd64
 Context:           default

Server:
 Engine:
  Version:          28.2.2
  API version:      1.50 (minimum version 1.24)
  Go version:       go1.23.1
  Git commit:       28.2.2-0ubuntu1~24.04.1
  Built:            Wed Sep 10 14:16:39 2025
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          1.7.28
  GitCommit:        
 runc:
  Version:          1.3.3-0ubuntu1~24.04.3
  GitCommit:        
 docker-init:
  Version:          0.19.0
  GitCommit:        ]

## Hello World Test
[
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/]

## Postgres Container

Command used:
docker run -d --name pg-prework -e POSTGRES_PASSWORD=prework -p 5432:5432 postgres:15-alpine

Startup Logs
[The files belonging to this database system will be owned by user "postgres".
This user must also own the server process.

The database cluster will be initialized with locale "en_US.utf8".
The default database encoding has accordingly been set to "UTF8".
The default text search configuration will be set to "english".

Data page checksums are disabled.

fixing permissions on existing directory /var/lib/postgresql/data ... ok
creating subdirectories ... ok
selecting dynamic shared memory implementation ... posix
selecting default max_connections ... 100
selecting default shared_buffers ... 128MB
selecting default time zone ... UTC
creating configuration files ... ok
running bootstrap script ... ok
sh: locale: not found
2026-03-05 08:00:12.259 UTC [35] WARNING:  no usable system locales were found
performing post-bootstrap initialization ... ok
initdb: warning: enabling "trust" authentication for local connections
initdb: hint: You can change this by editing pg_hba.conf or using the option -A, or --auth-local and --auth-host, the next time you run initdb.
syncing data to disk ... ok


Success. You can now start the database server using:

    pg_ctl -D /var/lib/postgresql/data -l logfile start

waiting for server to start....2026-03-05 08:00:13.129 UTC [41] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-05 08:00:13.131 UTC [41] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-05 08:00:13.138 UTC [44] LOG:  database system was shut down at 2026-03-05 08:00:12 UTC
2026-03-05 08:00:13.143 UTC [41] LOG:  database system is ready to accept connections
 done
server started

/usr/local/bin/docker-entrypoint.sh: ignoring /docker-entrypoint-initdb.d/*

waiting for server to shut down....2026-03-05 08:00:13.230 UTC [41] LOG:  received fast shutdown request
2026-03-05 08:00:13.233 UTC [41] LOG:  aborting any active transactions
2026-03-05 08:00:13.235 UTC [41] LOG:  background worker "logical replication launcher" (PID 47) exited with exit code 1
2026-03-05 08:00:13.235 UTC [42] LOG:  shutting down
2026-03-05 08:00:13.237 UTC [42] LOG:  checkpoint starting: shutdown immediate
2026-03-05 08:00:13.247 UTC [42] LOG:  checkpoint complete: wrote 3 buffers (0.0%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.003 s, sync=0.002 s, total=0.012 s; sync files=2, longest=0.001 s, average=0.001 s; distance=0 kB, estimate=0 kB
2026-03-05 08:00:13.251 UTC [41] LOG:  database system is shut down
 done
server stopped

PostgreSQL init process complete; ready for start up.

2026-03-05 08:00:13.352 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-05 08:00:13.352 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-05 08:00:13.353 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-05 08:00:13.357 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-05 08:00:13.361 UTC [55] LOG:  database system was shut down at 2026-03-05 08:00:13 UTC
2026-03-05 08:00:13.367 UTC [1] LOG:  database system is ready to accept connections
2026-03-05 08:00:50.360 UTC [1] LOG:  received fast shutdown request
2026-03-05 08:00:50.362 UTC [1] LOG:  aborting any active transactions
2026-03-05 08:00:50.364 UTC [1] LOG:  background worker "logical replication launcher" (PID 58) exited with exit code 1
2026-03-05 08:00:50.364 UTC [53] LOG:  shutting down
2026-03-05 08:00:50.366 UTC [53] LOG:  checkpoint starting: shutdown immediate
2026-03-05 08:00:50.380 UTC [53] LOG:  checkpoint complete: wrote 41 buffers (0.3%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.004 s, sync=0.005 s, total=0.016 s; sync files=11, longest=0.002 s, average=0.001 s; distance=229 kB, estimate=229 kB
2026-03-05 08:00:50.385 UTC [1] LOG:  database system is shut down

PostgreSQL Database directory appears to contain a database; Skipping initialization

2026-03-05 08:00:57.631 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-05 08:00:57.631 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-05 08:00:57.632 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-05 08:00:57.635 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-05 08:00:57.641 UTC [30] LOG:  database system was shut down at 2026-03-05 08:00:50 UTC
2026-03-05 08:00:57.646 UTC [1] LOG:  database system is ready to accept connections
2026-03-05 08:05:57.184 UTC [28] LOG:  checkpoint starting: time
2026-03-05 08:05:59.933 UTC [28] LOG:  checkpoint complete: wrote 30 buffers (0.2%); 0 WAL file(s) added, 0 removed, 0 recycled; write=2.733 s, sync=0.007 s, total=2.750 s; sync files=7, longest=0.005 s, average=0.001 s; distance=129 kB, estimate=129 kB]

Startup confirmation line found:
LOG: database system is ready to accept connections

## Stop and Restart
pg-prework
pg-prework

## Issues Encountered
None