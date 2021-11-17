# Configuration

## Available options

Run `pboted --help` to show builtin help message (default value of option will be shown in braces).

### General options


| Option     | Description                        |
|------------|------------------------------------|
| conf       | Config file (default: ~/.pboted/pboted.conf or /etc/pboted/pboted.conf). This parameter will be silently ignored if the specified config file does not exist. |
| pidfile    | Where to write pidfile (default: pboted.pid) |
| daemon     | pboted will go to background after start |
| service    | pboted will use system folders like '/var/lib/pboted' |
| log        | Logs destination: stdout, file, syslog (stdout if not set or invalid) (if daemon, stdout/unspecified are replaced by file in some cases) |
| logfile    | Path to logfile (default - autodetect) |
| loglevel   | Log messages above this level (debug, info, warn, error, none; default - info) |
| logclftime | Write full CLF-formatted date and time to log (default: write only time) |
| host       | pboted external IP for incoming connections |
| port       | UDP port to listen for incoming connections |
| storage    | Limit for local storage usage (default: 50 MB) |

!!! note "Note"

    `datadir` and `service` options are only used as arguments for pboted, these options have no effect when set in `pboted.conf`.


### SAM

| Option      | Description                          |
|-------------|--------------------------------------|
| sam.name    | If SAM is enabled. true by default   |
| sam.address | I2P SAM address (default: 127.0.0.1) |
| sam.tcp     | I2P SAM TCP port (default: 7656)     |
| sam.udp     | I2P SAM UDP port (default: 7655)     |
| 

### Bootstrap

| Option            | Description                        |
|-------------------|------------------------------------|
| bootstrap.address | These are the nodes with high uptime and the most information about peers in the network. To get started, you need at least one node that supports protocol version 4 or higher. Each line should be a I2P destination key in Base64 format. |

You can specify this parameter multiple times with different addresses.   
For example: 

```
[bootstrap]
address = <first address>
address = <second address>
...
address = <N-th address>
```

### SMTP

| Option       | Description                              |
|--------------|------------------------------------------|
| smtp.enabled | Allow connect via SMTP (default: true).  |
| smtp.address | SMTP listen address (default: 127.0.0.1) |
| smtp.port    | SMTP listen TCP port (default: 25)       |

### POP3

| Option       | Description                              |
|--------------|------------------------------------------|
| pop3.enabled | Allow connect via POP3 (default: true).  |
| pop3.address | POP3 listen address (default: 127.0.0.1) |
| pop3.port    | POP3 listen port (default: 110)          |
