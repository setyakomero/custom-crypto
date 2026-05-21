# custom-crypto-min.js

Lightweight RSA + HMAC utility for:

- Postman
- Browser
- Node.js

Built using:

- jsrsasign
- esbuild

This project provides:

- RSA Public Decrypt
- HMAC SHA512 Generator
- Minimal bundle for Postman usage
- No Node.js `crypto` dependency

---

# Features

- Pure JavaScript
- Postman compatible
- Browser compatible
- Node.js compatible
- Lightweight bundle
- RSA PKCS#1 unpadding support
- HMAC SHA512 support

---

# Functions

## decryptAccessToken(encryptedToken, publicKey)

Decrypt RSA token using public key.

### Parameters

| Name           | Type   | Description                                 |
| -------------- | ------ | ------------------------------------------- |
| encryptedToken | string | Base64 encrypted token                      |
| publicKey      | string | Base64 public key without PEM header/footer |

### Example

```javascript
const result =
    decryptAccessToken(
        encryptedToken,
        publicKey
    );

console.log(result);
```

---

## generateHmacSha512Hex(payload, secret)

Generate HMAC SHA512 hex digest.

### Parameters

| Name    | Type   | Description  |
| ------- | ------ | ------------ |
| payload | string | Data payload |
| secret  | string | Secret key   |

### Example

```javascript
const signature =
    generateHmacSha512Hex(
        payload,
        secret
    );

console.log(signature);
```

---

```bash
```

---

# Usage

## Node.js

```javascript
require('./custom-crypto-min.js');

console.log(
    typeof decryptAccessToken
);

console.log(
    typeof generateHmacSha512Hex
);
```

---

## RSA Decrypt Example

```javascript
require('./custom-crypto-min.js');

const encrypted =
`A9mqXafgf0yZeNz4oR7ywFwC97vz8XyoQmAKYihER/8Ybx9b3leAO/TRhrWZjXgNkBx1AVg+n4SUS9MEecgOhOs=`;

const publicKey =
`MFwwDQYJKoZIhvcNAQEBBQADSwAwSAJBBV2J2TGs4a1edZasjS3p/L2eKIHI0P282qE796htHPnJyCs1zZnd1yjSt4GxShUJJ6VEy98/u4JzsUqUBLjj8fcCAwEAAQ==`;

const result =
    decryptAccessToken(
        encrypted,
        publicKey
    );

console.log(result);
```

---

## HMAC SHA512 Example

```javascript
require('./custom-crypto-min.js');

const signature =
    generateHmacSha512Hex(
        'hello',
        'secret'
    );

console.log(signature);
```

---

# Postman Usage

## Save Script to Globals

```javascript
pm.globals.set(
    'custom-crypto',
    'MINIFIED_SCRIPT_HERE'
);
```

---

## Load Script

```javascript
eval(
    pm.globals.get(
        'custom-crypto'
    )
);
```

---

## Example Usage in Postman

```javascript
eval(
    pm.globals.get(
        'custom-crypto'
    )
);

const result =
    decryptAccessToken(
        encryptedToken,
        publicKey
    );

console.log(result);
```

---

# Internal Dependencies

Minimal dependencies used from jsrsasign:

- BigInteger
- KEYUTIL
- RSAKey
- KJUR.crypto.Mac
- b64tohex
- hextoutf8

---

# Supported Padding

PKCS#1:

- Type 01
- Type 02

---

# Notes

- Public key must be Base64 without PEM wrapper.
- Encrypted token must be Base64 encoded.
- Bundle generated using esbuild IIFE format.
- Designed for lightweight Postman execution.

---

# License

MIT License

---

# Author

@joko\_prasetyo95

