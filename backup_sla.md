Coverage: Databases backup MySQL agama database and InfluxDB database.
RPO: Full backups are created daily at 00:05-00:25 for InfluxDB and at 00:30-00:40 for MySQL. Incremental backups are done daily excluding Sunday.
Retention: Backup versions are stored for 24 hours before they get updated with new backup versions.
Usability checks: Verification of the backup usability may be done by restoring the backups, following the restoration rules listed in the backup_restore.md file.
Restoration criteria: Unpredicted data loss, server failure, the need to retrieve the old data.
RTO: RTO is up to 1 hour, meaning up to 1 hour of time is needed for completing the successful recovery.
