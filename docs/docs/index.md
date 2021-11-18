# pboted

pboted (Plus Bote Daemon) - is a standalone C++ implementation of I2P-Bote protocol.

I2P-Bote is a server-less encrypted KademliaDHT-based email protocol.   
You can find more details it [Bote](devs/bote/v5/version5.md) section.

Interaction with the I2P network occurs through the [SAMv3](https://geti2p.net/ru/docs/api/samv3) interface.
Tested with [i2pd](https://github.com/PurpleI2P/i2pd) and [Java I2P](https://github.com/i2p/i2p.i2p).

## Features

- Sending and receiving emails
- Basic support for short recipient names
- Elliptic Curve encryption (ECDH-256/ECDSA-256/AES-256/SHA-256)
- Runnable as daemon or as user service
- SMTP / POP3 (basic support, work in progress)

## Planned Features

- Custom per identity/user email folders
- Sending email anonymously
- Delivery confirmation
- Sending and receiving via relays, similar to Mixmaster
- CLI interface and tools
- Interfaces for interaction with third-party applications (IMAP, etc.)

## Resources

- [Documentation](https://pboted.readthedocs.io/en/latest/)
- [Tickets/Issues](https://github.com/polistern/pboted/issues)
