# SMTP

_Tested with [Mozilla Thunderbird](https://www.thunderbird.net/en-US/)_

To be able to send email through SMTP you need to:

- Fill `[smtp]` section in [configuration file](../user-guide/configuration.md#smtp):

```
[smtp]
enabled = true
address = 127.0.0.1
port = 25
```

- Restart the **pboted** to apply the settings
- After loading, you be able to connect to the specified SMTP port manually or with your mail client.

## How to compose email

### FROM

There are 2 options for how this field might look.

#### 1. classic

In this case, the address consists of three parts, something like this:

`NAME <IDENTITY_NAME@DOMAIN>`

The NAME part is optional.   
The IDENTITY_NAME part should be the name of the used Bote identity.   
The DOMAIN part can be any valid domain.

For example:

`John Doe <johnd@bote.i2p>`

#### 2. Bote style

In this case, the address consists of two parts, something like this:

`IDENTITY_NAME <BOTE_ADDRESS>`

The IDENTITY_NAME part should be the name of the used Bote identity.   
The BOTE_ADDRESS part should be Bote address.

For example:

`johnd <24noEIMPvV9CEwrSWQtIsTA7balaZ80ZOGRBAzrsBl5nv9xud~k28d9TQIgXmyyCYtHl8PJASAFDeefSc6EJ81>`

### TO

Very similar to field FROM with one amendment for option 1:   
The <IDENTITY_NAME@DOMAIN> must be in the address book for replacement.

For example, if you have this record in addressbook:

```
johnd1@bote.i2p;John Doe 1;24noEIMPvV9CEwrSWQtIsTA7balaZ80ZOGRBAzrsBl5nv9xud~k28d9TQIgXmyyCYtHl8PJASAFDeefSc6EJ81
```

You can fill TO like this:

`TO: John Doe <johnd1@bote.i2p>`
