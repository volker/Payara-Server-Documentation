# Contents
* [1. Overview](#1-overview)
* [2. Documentation Conventions](#2-documentation-conventions)
* [3. Starting and Stopping the Asadmin Recorder](#3-starting-and-stopping-the-asadmin-recorder)
* [4. Configuring the Asadmin Recorder](#4-configuring-the-asadmin-recorder)
* [5. Running the Generated Scripts](#5-running-the-generated-scripts)
* [6. Appendices](#6-appendices)
  * [6.1 Asadmin Commands](#61-asadmin-commands)

# 1. Overview
This page will cover how to use the Asadmin Recorder feature of Payara Server.  

This feature allows you to record the actions you take in the admin console as asadmin commands, aiding with automating or reproducing your setup across multiple Payara Server installations.

# 2. Documentation Conventions
* References to the _domain directory_ refers to the directory where the Payara Server domain is located.

# 3. Starting and Stopping the Asadmin Recorder
From the admin console, you should be able to see a button labelled _Enable Asadmin Recorder_ or _Disable Asadmin Recorder_, depending on whether or not the asadmin recorder feature is enabled or not. Clicking this button will enable or disable the asadmin recorder feature respectively.

Once enabled, actions in the admin console that have a corresponding asadmin command will be recorded to a file. By default, this file is located in the domain directory, and is called _asadmin-commands.txt_.

Once enabled or disabled, the asadmin recorder will remain enabled/disabled until specifically enabled or disabled again through clicking this button or using the appropriate asadmin command - the asadmin recorder will remain enabled or disabled across server restarts.

You can also enable or disable the asadmin recorder on its configuration page (detailed in section [4.](#4-configuring-the-asadmin-recorder)), or by using the following asadmin commands:

* `enable-asadmin-recorder` - Enables the asadmin recorder.
* `disable-asadmin-recorder` - Disables the asadmin recorder.
* `set-asadmin-recorder-configuration --enabled true` - Alternative way of enabling the asadmin recorder.
* `set-asadmin-recorder-configuration --enabled false` - Alternative way of disabling the asadmin recorder.

# 4. Configuring the Asadmin Recorder
To configure the asadmin recorder, navigate to the following page in the admin console: _server > Asadmin Recorder_
You will be presented with a series of configuration options:

* _Enabled_ - Sets whether the asadmin recorder service should be enabled or disabled.
* _Filter Commands_ - Sets whether or not to exclude the asadmin commands and regular expressions listed in the _Filtered Commands_ setting from being recorded.
* _Output Location_ - The absolute file path for the asadmin commands to be written to. This defaults to a file called _asadmin-commands.txt_ in the domain directory.
* _Filtered Commands_ - A comma separated list of asadmin commands and regular expressions to be excluded from being recorded if the _Filter Commands_ option is enabled.

The default regular expressions and asadmin commands set in the _Filtered Commands_ option are a selection of commands and regular expressions that are typically not needed for any automation purposes, yet are still sometimes called by commands and through navigation of the admin console. If you remove any of these commands from the filtered commands list, or choose not to filter any commands at all, the asadmin commands script is liable to get filled up with these commands. Due to this, it is advised that you only add to this list, only removing the defaults if you really need to.

Be sure to click on the _Save_ button to have any changes you make take effect.

In addition to using the admin console, you can configure the asadmin recorder service using the `set-asadmin-recorder-configuration` command. The command takes the following parameters:

* `--enabled` - Enables or Disables the Asadmin Recorder service.
* `--outputLocation` - Specifies the absolute file path of where the recorded asadmin commands will be written to.
* `--filterCommands` - Specifies whether or not the commands specified with the _--filteredcommands_ option should be excluded from being recorded or not.
* `--filteredCommands` - A comma separated list of asadmin commands and regular expressions to exclude from being recorded.

As an example, the following will enable the asadmin recorder, set the output location to /home/user/asadmin-commands.txt, and prevent the _start-instance_ command from being recorded (in addition to the defaults):

```Shell
asadmin set-asadmin-recorder-configuration --enabled true --outputLocation /home/user/asadmin-commands.txt --filterCommands true --filteredCommands "version,_(.*),list(.*),get(.*),uptime,enable-asadmin-recorder,disable-asadmin-recorder,set-asadmin-recorder-configuration,asadmin-recorder-enabled,start-instance"
```

# 5. Running the Generated Scripts
Documentation on running asadmin scripts can be found in the [core documentation](documentation/core-documentation/core-documentation.md), under the _Run a Set of asadmin Subcommands From a File_ section.

# 6. Appendices
## 6.1 Asadmin Commands

| Command | Description | Options |
|------------------------------------|--------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| get-asadmin-recorder-configuration | Returns the current configuration of the Asadmin Recorder service. | None |
| set-asadmin-recorder-configuration | Configures the Asadmin Recorder service. | `--enabled` - Enables or Disables the Asadmin Recorder service.<br>`--outputLocation` - Specifies the absolute file path of where the recorded asadmin commands will be written to.<br>`--filterCommands` - Specifies whether or not the commands specified with the _--filteredcommands_ option should be excluded from being recorded or not.<br>`--filteredCommands` - A comma separated list of asadmin commands and regular expressions to exclude from being recorded. |
| enable-asadmin-recorder | Enables the Asadmin Recorder service with it's current configuration settings. | None |
| disable-asadmin-recorder | Disables the Asadmin Recorder service. | None |
| asadmin-recorder-enabled | Returns whether or not the Asadmin Recorder service is enabled. | None |

