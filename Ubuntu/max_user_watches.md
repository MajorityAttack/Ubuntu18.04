### how to increacing max_user_watches ?

sysctl -w writes kernel parameter values to the corresponding keys under /proc/sys:
```sh
sudo sysctl -w fs.inotify.max_user_watches=524288
```
writes 524288 to /proc/sys/fs/inotify/max_user_watches. 

```sh
sysctl -p
```

loads settings from a file, either /etc/sysctl.conf (the default), or whatever file is specified after -p.

The difference between both approaches, beyond the different sources of the parameters and values they write, is that -w only changes the parameters until the next reboot, whereas values stored in /etc/sysctl.conf will be applied again every time the system boots. My usual approach is to use -w to test values, then once I’m sure the new settings are OK, write them to /etc/sysctl.conf or a file under /etc/sysctl.d (usually /etc/sysctl.d/local.conf).

See the sysctl and sysctl.conf manual pages (man sysctl and man sysctl.conf on your system) for details.

https://unix.stackexchange.com/questions/444998/how-to-set-and-understand-fs-notify-max-user-watches
