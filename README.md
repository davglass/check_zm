Zagios Plugin for ZoneMinder
============================

Simple script to check that your [ZoneMinder](https://www.zoneminder.com/) server is up and running.

If it detects that the service is down, it will ping the API and attempt to start it again.

usage
=====

`commands.cfg`

```
define command {
    command_name    check_zm
    command_line    /usr/local/nagios/libexec/check_zm -H http://192.168.1.112/zm/ -u username -p password
}
```

The the service for the host:

```
define service {
        use                             local-service
        host_name                       192.168.1.112
        service_description             ZoneMinder
        check_command                   check_zm
}
```
