# Feature Improvements

Payara 4.1.144 ships with support for setting the schema in JBatch  for Derby (GlassFish-21041). This can be found in the Admin Console under server > Batch > Configuration

Tyrus has also been updated to version 1.8.3.

# Bug Fixes

Payara 4.1.144 was built upon GlassFish 4.1, so contains all of the bug fixes and improvements to be found there. The release notes for GlassFish 4.1 can be found here.

In addition to the fixes incorporated into GlassFish 4.1, Payara 4.1.144 also has the following additional bug fixes:

* GlassFish-21242 - Glassfish throws NPE with System.out.println(null)
* GlassFish-21018 - set-batch-runtime-configuration change not reflected in admin gui
* GlassFish-21138 - After editing Availability service in configurations domain.xml corrupted
* GlassFish-20610 - Fix spurious log messages on boot of AMX
* GlassFish-21239 - Monitoring is not displayed in the console if the administrator password is not blank
* GlassFish-20718 - Write to System Log option do not send log on localhost udp port 514
* GlassFish-21175 - Glassfish Hang when Timer application configured with XA Datasource
* GlassFish-21098 - GlassFish 4.x can't be built using jdk8
* GlassFish-21159 - X-PoweredBy sent even when disabled in the console
* GlassFish-20895 - @ForeignKey creates wrong ALTER TABLE statement