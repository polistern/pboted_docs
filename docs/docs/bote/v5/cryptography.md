# 7. Cryptography (DRAFT)

## 7.1. Asymmetric encryption and signing

Encryption and signature algorithms:

| ID | Crypto           | Signing     | Symmetric | Hash    | Java-Bote | pboted |
|----|------------------|-------------|-----------|---------|-----------|--------|
| 1  | ElGamal-2048     | DSA-1024    | AES-256   | SHA-256 | yes       | never  |
| 2  | ECDH-256         | ECDSA-256   | AES-256   | SHA-256 | yes       | yes    |
| 3  | ECDH-521         | ECDSA-521   | AES-256   | SHA-512 | yes       | yes    |
| 4  | NTRUEncrypt-1087 | GMSS-512    | AES-256   | SHA-512 | yes       | no     |
| 5  | X25519           | ED25519     | AES-256   | SHA-512 | no        | yes    |

## 7.2. Password Encryption

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

## 7.3. Fingerprints For Directory Entries

ToDo: Looks specific to Java app, remove from protocol description

TODO
H = scrypt(name, dest, zuf.wert); die letzten 8 Binärstellen von H müssen 0 sein
13*7+22+18 = 131
