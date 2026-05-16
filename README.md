# Config Repo

Centralized application configuration for environment-specific database settings.

## Files

| File | Purpose |
| --- | --- |
| `cloud-config.properties` | Default configuration used when no profile-specific file overrides it. |
| `cloud-config-dev.properties` | Development environment configuration. |
| `cloud-config-qa.properties` | QA environment configuration. |
| `cloud-config-prod.properties` | Production environment configuration. |

## Properties

Each configuration file defines the same MongoDB-related keys:

| Property | Description |
| --- | --- |
| `jsp.dbName` | Database name used by the application. |
| `jsp.dbURI` | MongoDB connection URI. |

## Current Values

| Environment | Database Name | Database URI |
| --- | --- | --- |
| Default | `default_db_name` | `default_db_uri` |
| Dev | `video-platform-db` | `mongodb://localhost:27017/video-platform-db` |
| QA | `db_name` | `mdb_uri` |
| Prod | `db_name` | `db_uri` |

## Updating Configuration

1. Edit the file that matches the target environment.
2. Keep property names consistent across all environment files.
3. Do not commit real production secrets or credentials unless this repository is stored and accessed securely.
4. Restart or refresh the consuming application after changing configuration values.

## Spring Profile Naming

The file names follow the Spring Cloud Config convention:

```text
cloud-config-{profile}.properties
```

For example, activating the `dev` profile uses values from `cloud-config-dev.properties` in addition to defaults from `cloud-config.properties`.
