# Files (DRAFT)

## Identities file

Stores all email identities the local user has created.   
The file uses the Java Properties format, and can be read into / written out from a Java Properties object.

The following property keys are currently stored and recognized (N is an integer index):

| Field                | Description                                                |
|----------------------|------------------------------------------------------------|
|identityN.publicName  | The public name of the identity, included in emails.       |
|identityN.key         | Base64 of the identity keys.                               |
|identityN.salt        | Salt used to generate a fingerprint.                       |
|identityN.description | Description of the identity, only displayed locally.       |
|identityN.picture     | Base64 of byte[] containing picture data                   |
|identityN.text        | Text associated with the identity.                         |
|identityN.published   | Has the identity been published to the public addressbook? |

The base64 key contains two public keys (encryption+signing) and two private keys.

The identities file can optionally contain the property key "default", with its value set to an Email Destination (i.e. two public keys).   
If the Email Destination matches one of the identities, that identity is used as the default.

## Password Encryption

ToDo: Looks specific to Java app, remove from protocol description

The identities file, the address book, and all email files are encrypted with AES-256.   
To generate the AES key from the password, scrypt (http://www.tarsnap.com/scrypt.html) is used.   
The file format is:

|Field | #bytes | Description                                   |
|------|--------|-----------------------------------------------|
|SOF   | 4      | Start of file, contains the characters "IBef" |
|VER   | 1      | Format version, must be 1                     |
|N     | 4      | scrypt CPU cost parameter                     |
|r     | 4      | scrypt memory cost parameter                  |
|p     | 4      | scrypt parallelization parameter              |
|SALT  | 32     | Salt for scrypt                               |
|IV    | 32     | IV for AES                                    |
|DATA  |        | The encrypted data                            |

Parameters N through SALT are cached in a file named derivparams so all encrypted files can use the same key derivation parameters.   
This makes decryption much faster because the key only needs to be derived once per session.

## Included .jar files and third-party source code

ToDo: Looks specific to Java app, remove from protocol description 

- bcprov-jdk15on-152.jar     The BouncyCastle library and SecurityProvider.
- mailapi-1.5.4.jar          Part of JavaMail 1.5.4
- lzma-9.20.jar              An LZMA implementation from http://www.7-zip.org/sdk.html
- ntruenc-1.2.jar            An NTRU implementation from http://sf.net/projects/ntru/ (only the NTRUEncrypt part, not NTRUSign)
- flexi-gmss-1.7p1.jar       A stripped down and patched version of the FlexiProvider sources (http://www.flexiprovider.de/), containing only the classes needed for GMSS. The patch consists of a modified de.flexiprovider.core.CoreRegistry and de.flexiprovider.api.Registry and its purpose is to reduce dependencies on classes not related to GMSS.
- scrypt-1.4.0.jar           An scrypt implementation from https://github.com/wg/scrypt/
