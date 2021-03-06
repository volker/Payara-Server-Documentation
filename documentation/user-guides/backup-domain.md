# Payara Server Domain Backup

Oracle GlassFish 3 had a built-in automatic backup facility using the asadmin command `create-backup-config`. This allowed you to specify a schedule for when to backup, where to place the backed up file, and how many backups to keep.

This is no longer present in GlassFish or Payara Server, since it was a commercial feature that was never open-sourced, but its effects can be reproduced without much effort using the `backup-domain` command and some scheduling software (crontab, for example)

Since the domain directory is where all of the user configuration of Payara Server is kept, we can consider this to be separate to the installation files that Payara Server uses to run the app server itself. We can backup the domain using the `asadmin backup-domain` command as follows:

```
asadmin backup-domain --backupDir /path/to/backup/directory myDomain
```

The effect of this command is to create a full backup of the domain directory. To complete the command, however, **the domain must be stopped**. This will mean that any application deployed to the DAS is unavailable while the backup takes place.

The job of running this backup command on a given schedule and managing the resulting backed up files needs to be done by a script external to Payara Server.


----

#### See Also

* [Restore a Payara Server Domain](restore-domain.md)
* [Upgrade Payara Server](upgrade-payara.md)