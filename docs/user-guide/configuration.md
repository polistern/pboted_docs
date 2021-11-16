# Configuration

## The pboted needs I2P router

- Install and run i2pd
- Enable SAM API in i2pd. Edit in i2pd.conf:

```
[sam]
enabled = true
```

- Restart i2pd   
- Local TCP port 7656 and UDP port 7655 should be available

## User service configuration

- Copy example config from `contrib/pboted.conf` to `~/.pboted/pboted.conf`:

```
cp contrib/pboted.conf ~/.pboted/pboted.conf`
```

- Edit the config to suit your needs. The file is well documented, comments will help you.
- Now you can run application:

```
./pboted --conf ~/.pboted/pboted.conf
```

## Unix daemon configuration [recommended]

- Create `/etc/pboted` directory:

```
sudo mkdir /etc/pboted
```

- Copy example config from `contrib/pboted.conf` to `~/.pboted/pboted.conf`:

```
sudo cp contrib/pboted.conf /etc/pboted/pboted.conf`
```

- Edit the config to suit your needs. The file is well documented, comments will help you.
- Create user, data and logs directories:

```
sudo useradd pboted -r -s /usr/sbin/nologin
sudo mkdir /var/lib/pboted
sudo chown -R pboted: /var/lib/pboted
sudo mkdir /var/log/pboted
sudo chown -R pboted: /var/log/pboted
```

- Copy example systemd service from `contrib/pboted.service` to `/lib/systemd/system/pboted.service`:

```
sudo cp contrib/pboted.service /lib/systemd/system/pboted.service`
```

- Reload daemons configuration and start unit:

```
sudo systemctl daemon-reload
sudo systemctl start pboted.service
```

- Now you can see in log files that all works. Also, you can see the status of the SAM session in the I2P Router console.

# Usage

You may need the utilities from the `utils` directory to work with **pboted**.   
In the future, their list will grow.   
There are plans to transfer all means for interaction into a separate CLI utility.

You can only continue to use your Java I2P-Bote identities if:

- your address is created using the ECDH-256/ECDSA-256/AES-256/SHA-256 algorithm (others are not supported yet)
- identities file is not encrypted (encrypted files are not supported yet)

## Sending email

### SMTP

To be able to send email through SMTP you need to:

- Fill [smtp] section in configuration file:

```
[smtp]
enabled = true
address = 127.0.0.1
port = 25
```

- Restart the **pboted** to apply the settings
- After loading, you be able to connect to the specified SMTP port manually or with your mail client

### Via `outbox` directory 

- Prepare plain test message
- Format it with `message_formatter`
- Put result file to `outbox` directory in pboted working directory
- pboted will automatically check `outbox` and send email
- After sending email file will be moved to `sent` directory

## Receiving email

After starting with a generated identity the application will begin its normal job of searching for mail.  
If mail for identity are found, they will be placed in the `inbox` directory.

### POP3

To be able to receive email through POP3 you need to:

- Fill [pop3] section in configuration file:

```
[pop3]
enabled = true
address = 127.0.0.1
port = 110
```

- Restart the **pboted** to apply the settings
- After loading, you be able to connect to the specified POP3 port manually or with your mail client.
