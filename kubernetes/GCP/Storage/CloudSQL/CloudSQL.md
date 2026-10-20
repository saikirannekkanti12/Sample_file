# Google Cloud SQL — WordPress Lab

## Overview

Configure a Cloud SQL MySQL instance and connect a WordPress application using:

- Cloud SQL Auth Proxy
- Private IP connectivity

## Architecture

```text
WordPress Application
        |
        +---- Cloud SQL Auth Proxy ----> Cloud SQL
        |
        +---- Private IP --------------> Cloud SQL
```

## Task 1: Enable APIs

Enable the Service Networking API in Google Cloud Console.

## Task 2: Create Cloud SQL Instance

| Property | Value |
|---|---|
| Instance ID | `wordpress-db` |
| Database | MySQL 8.0 |
| Region | `us-east1` |
| Database name | `wordpress` |
| Private IP | Enabled |

## Task 3: Configure Cloud SQL Proxy

Download the proxy:

```bash
wget https://dl.google.com/cloudsql/cloud_sql_proxy.linux.amd64 -O cloud_sql_proxy
chmod +x cloud_sql_proxy
```

Set the instance connection name:

```bash
export SQL_CONNECTION="<INSTANCE_CONNECTION_NAME>"
```

Start the proxy:

```bash
./cloud_sql_proxy -instances=$SQL_CONNECTION=tcp:3306 &
```

Expected output:

```text
Listening on 127.0.0.1:3306
Ready for new connections
```

## Task 4: Connect WordPress

Configure the database settings:

| Property | Value |
|---|---|
| Database Name | `wordpress` |
| Username | `root` |
| Database Host | `127.0.0.1` |

Use your configured database password.

## Task 5: Connect Using Private IP

Use the Cloud SQL instance's internal IP as the database host.

Private IP connectivity avoids routing database traffic through the public internet, provided the network connectivity is configured correctly.

## Key Learnings

- Cloud SQL provides managed relational databases.
- The Cloud SQL Auth Proxy provides an authenticated connection path.
- Private IP connectivity can reduce latency and public network exposure.
- Database credentials should be stored securely, not committed to GitHub.
