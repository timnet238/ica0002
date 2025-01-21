Coverage: Databases backup MySQL agama database and InfluxDB database.
RPO: For Influxdb full backups are created daily at 23:35, incremental backups are done from Monday to Saturday at 23:40. For Mysql the agama database is dumped to a file (agama.sql) daily at 23:05, full backups are created every Sunday at 23:15, incremental backups are done from Monday to Saturday at 23:25.
Retention: Backup versions are stored for 24 hours before they get updated with new backup versions.
Usability checks: Verification of the backup usability may be done by restoring the backups, following the restoration rules listed in the backup_restore.md file.
Restoration criteria: Unpredicted data loss, server failure, the need to retrieve the old data.
RTO: RTO is up to 1 hour, meaning up to 1 hour of time is needed for completing the successful recovery.
