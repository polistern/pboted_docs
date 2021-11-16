# SMTP

To be able to send email through SMTP you need to:

- Fill [smtp] section in configuration file:

```
[smtp]
enabled = true
address = 127.0.0.1
port = 25
```

- Restart the **pboted** to apply the settings
- After loading, you be able to connect to the specified SMTP port manually or with your mail client.
