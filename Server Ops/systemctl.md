## Enable a systemd unit while also starting it at the same time

```sh
systemctl enable --now some-service
```

will combine the enabling of the service unit and the starting, so you no longer have to type two commands to get something working following an install.
