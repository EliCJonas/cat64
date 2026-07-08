# cat64

A standalone command-line text encoder and decoder.

## Overview

`cat64` converts text into a numeric format using a custom encoding dictionary and can optionally encrypt the result using a 16-bit key.

Unlike earlier versions, `cat64` is self-contained and does not require the `writo64` Python module.

Features:

* Single-file executable
* Text encoding and decoding
* Random 16-bit key generation
* Custom encryption keys
* No external dependencies

## Installation

Copy the `cat64` file somewhere in your PATH:

```bash
sudo cp cat64 /usr/local/bin/cat64
```

Make it executable:

```bash
chmod +x cat64
```

Test:

```bash
cat64
```

## Usage

### Encode text

Generate a random key:

```bash
cat64 encode "hello" r
```

Example output:

```text
Cipher:
596329747797139...

Key:
48291
```

Save the key. It is required to decode the message.

---

Use a custom key:

```bash
cat64 encode "hello" 12345
```

---

Encode without encryption:

```bash
cat64 encode "hello" n
```

## Decode

Decode an encrypted message:

```bash
cat64 decode <cipher> <key>
```

Example:

```bash
cat64 decode 596329747797139... 48291
```

Output:

```text
hello
```

## Short Commands

Encode:

```bash
cat64 -e "hello" r
```

Decode:

```bash
cat64 -d <cipher> <key>
```

## Encryption

The encryption system uses a 16-bit integer key.

Encryption:

```text
cipher = ((data XOR key) * 65537) + key
```

Decryption:

```text
data = ((cipher - key) // 65537) XOR key
```

The key must be stored separately.

## Character Support

`cat64` supports:

* Uppercase letters
* Lowercase letters
* Numbers
* Spaces
* Common programming symbols

Unsupported characters will produce an error.

## Security Notice

`cat64` is designed for:

* Learning
* Experimentation
* Simple obfuscation

It is not intended as a replacement for modern encryption systems.

Do not use it for protecting sensitive information.

## Version

```text
1.0
```

