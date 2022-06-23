# 8. Glossary of Terms (DRAFT)

## 8.1 Email Destination

As the name implies, an Email Destination is an identifier by which somebody can be reached via I2P-Bote.

### Formats

#### Version 0

An Email Destination is a Base64 string containing a public encryption key and a signature verification key.   
Example of a 512-character Email Destination (ElGamal-2048/DSA-1024):
  
```
  uQtdwFHqbWHGyxZN8wChjWbCcgWrKuoBRNoziEpE8XDt8koHdJiskYXeUyq7JmpG
  In8WKXY5LNue~62IXeZ-ppUYDdqi5V~9BZrcbpvgb5tjuu3ZRtHq9Vn6T9hOO1fa
  FYZbK-FqHRiKm~lewFjSmfbBf1e6Fb~FLwQqUBTMtKYrRdO1d3xVIm2XXK83k1Da
  -nufGASLaHJfsEkwMMDngg8uqRQmoj0THJb6vRfXzRw4qR5a0nj6dodeBfl2NgL9
  HfOLInwrD67haJqjFJ8r~vVyOxRDJYFE8~f9b7k3N0YeyUK4RJSoiPXtTBLQ2RFQ
  gOaKg4CuKHE0KCigBRU-Fhhc4weUzyU-g~rbTc2SWPlfvZ6n0voSvhvkZI9V52X3
  SptDXk3fAEcwnC7lZzza6RNHurSMDMyOTmppAVz6BD8PB4o4RuWq7MQcnF9znElp
  HX3Q10QdV3omVZJDNPxo-Wf~CpEd88C9ga4pS~QGIHSWtMPLFazeGeSHCnPzIRYD
```

Example of a 86-character Email Destination (ECC-256):

```
  1Lcvly8no5of6juJKxqy-xA-MStM2c2XKorepH1oqs5yKBkg9-ZcG4G4kZY1E~2672cMA806l9EicQLmlehB1m
```

Used by **pboted** and **I2P-Bote**

Destination type can only be determined by the length of the base64 string:

| ID | Public    | Private  |
|----|-----------|----------|
| 1  | 512       | 880      |
| 2  | 86        | 172      |
| 3  | 174       | 348      |
| 4  | 2079      | 97813    |

#### Version 1

After the introduction of new, more modern algorithms, the question arose of the ambiguity of determining the type of key by its length in the form of base64.  
A more comprehensive format has been developed that will later allow combinations of different types of keys, not just predefined ones.

Used by **pboted**

Template:
`<data format>.<encoded data>`

- data format - Can be **b32** (`base32`) or **b64** (`base64`) for now
- encoded data - Can be bytes with **public** or **private (full)** destination (identity)
  - Public:
    - data[0] - format version (`1` for following (current) data structure)
    - data[1] - cryptography algorithm type
    - data[2] - signing algorithm type
    - data[3] - symmetric encryption algorithm type
    - data[4] - hash algorithm type
    - data[5-N] - crypto public key
    - data[N-M] - signing public key
  - Private (full):
    - data[0] - format version (`1` for following (cuurent) data structure)
    - data[1] - cryptography algorithm type
    - data[2] - signing algorithm type
    - data[3] - symmetric encryption algorithm type
    - data[4] - hash algorithm type
    - data[5-N] - crypto public key
    - data[N-M] - signing public key
    - data[M-X] - crypto private key
    - data[X-Y] - signing private key

## 8.2 Email Address

Email Addresses in I2P-Bote are shortcuts for Email Destinations.   
Email Address <--> Email Destination mappings are stored in two places:
- local address book;
- distributed address directory.

## 8.3 Email Identity

An Email Identity is an Email Destination plus a name you want to be known as when you use that identity.   
Technically speaking, an Email Identity consists of four things:

* An Email Destination (i.e. two public keys)
* The two private keys for the Email Destination
* A public name which is shown to other people in emails
* A description which is not shown to anybody but you
  It helps you remember which Email Identity you use for which purpose.

An email identity is not required for sending emails (in that case only "Anonymous" can be selected in the "sender" field).

## 8.4 I2P destination

The address of a I2P-Bote node on the I2P network. There is normally no need to know it.   
I2P destinations and Email Destinations look similar, but are completely independent of each other.
