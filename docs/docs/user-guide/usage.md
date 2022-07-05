# Usage

You may need the utilities from the [pboted-tools](https://github.com/polistern/pboted-tools/) repository to work with **pboted**.   
In the near future, this functionality will be implemented as a [CLI utility](https://github.com/polistern/pbotectl).

You can only continue to use your `Email identities` from **Java Bote** if:

- your address is created using the one of the follow algorithm (others are not supported yet):
    - `ECDH-256/ECDSA-256/AES-256/SHA-256`
    - `ECDH-521/ECDSA-521/AES-256/SHA-512` 
- identities file is not encrypted (encrypted files are not supported yet)

## Create Bote identity

See [create_identity](https://github.com/polistern/pboted-tools/tree/main/create_identity)

## Sending email

!!! note "Note"

    After successful sending, the email file will be modified and moved to the `sent` directory

### SMTP

See [SMTP](../tutorials/SMTP.md)

### Via `outbox` directory 

- Prepare plain test message
- Format it with [message_formatter](https://github.com/polistern/pboted-tools/tree/main/message_formatter)
- Put result file to `outbox` directory in pboted working directory
- pboted will automatically check `outbox` and send email

## Receiving email

After starting with a generated identity the application will begin its normal job of searching for mail.  

### Via `inbox` directory 

If mail for identity are found, they will be placed in the `inbox` directory as a plain text file.

### POP3

See [POP3](../tutorials/POP3.md)
