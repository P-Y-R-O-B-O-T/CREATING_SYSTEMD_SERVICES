# CREATING SYSTEMD SERVICE

![](ZZZ/ZZZ/jpeg)

* A systemd unit refers to any resource that the system knows how to operate upon and manage.

* two locations store the systemd files
- `/etc/systemd/system` used by normal software services
- `/lib/systemd/system` system copy of services

# BASIC STRUCTURE OF SERVICE FILE

```service
[Unit] # Unit section, compulsory to add

Description=Describe the service here

Documentation=<link to service docs>

# Requires=<services name> # Specify service to start along with this service, if they don't start, this service fails
# Wants=<services name> # Similar to Requires, but the service do not fail
# BindsTo=<services to attach with, if that service terminates, this also terminates>]
# After=<services that needs to be running before this service starts>]
# Before=<specify services that depends on this service, that will run only if this service is running>]
# Conflict=<list services that can never run while this one is running>]
# [Condition directive]
# [Assert directive]


[Service] # Service section, compulsory to add

# ExecStartPre=<commands> # Provide commands to be started before the main service starts

ExecStart=<main service command> # Define the main service command

# ExecReload=<command> # Define how to reload/restart the service, command necessary to reload the config of service if available

Type=<simple|forking|oneshot|dbus|notify|idle> # Specify type of service
Restart=<always|on-failure|on-abort|on-abnormal> # Define restart conditions

# ExecStartPost=<commands> # commands to be executed after the service is running
# ExecStop=<command> # Specify command needed to stop the service
# ExecStopPost=<commands> # Specify commands to execute after stop command above is executed
# RestartSec=<number> # Seconds to wait between attempts to restart the service
# TimeoutSec=<number> # Specify time for syatemd daemon to wait for service to come alive or get terminated on deactivation before it is marked failed or forcefullt killing
# RemainAfterExit=<yes|no> # When service needs to be considered as active even after exited, used with oneshot
# PIDFile=<path> # Used with forking type, path to pid of of the file which must contain PID of main child
# BusName=<bus name> # Dbus service name that the service will try to acquire when using the dbus service
# NotifyAccess=<main|none|all> # specify type of noticications to listen to


[Install] # Install section, optional

WantedBy=<milti-user.target is generally used>

# RequiredBy=<service> # Specify the service that requires this service else that service fails
# Alias=<name> # Specify alternative name for the service
# Also=<services> # allow services to be enabled or disabled as a set
```

## Steps
- Create a service file with `.service` extension
- Move it to systemd units directory for user units `/etc/systemd/system`
- Restart the systemd daemon using `systemctl daemon-reload`
- Manage the service using ``

## REFERENCES
- [Digital Ocean](https://www.digitalocean.com/community/tutorials/understanding-systemd-units-and-unit-files)
- [Opensource.com](https://opensource.com/article/20/5/systemd-units)
- [Stack Exchange](https://unix.stackexchange.com/questions/15348/writing-basic-systemd-service-files)
- [Linux Handbook](https://linuxhandbook.com/create-systemd-services/)
- []()
