#JMX Monitoring Service
_Payara Server 4.1.1.163 onwards_

With the release of Payara Server 163, Payara offers a JMX Monitoring Service. Once configured, Payara Server will monitor and log the values of attributes that have been listed for monitoring. The metrics are logged together in a single log message as a series of key-value pairs prefixed by the string `PAYARA-MONITORING:`. 

Payara uses the AMX API for working with JMX MBeans. AMX is not fully exposed by default and as such needs to be loaded to access most JMX MBean objects. The JMX Monitoring Service can be used without AMX but there is a limit to what can be monitored without it.
