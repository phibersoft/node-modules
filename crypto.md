# crypto

The crypto module provides cryptographic functionality that includes a set of wrappers for OpenSSL's hash, HMAC, cipher, decipher, sign and verify functions.

> Summary is **encryption and decryption**.
## Popular Functions

- [crypto.createHash](#cryptocreatehashalgorithm-options)
- [crypto.createCipheriv](#cryptocreatecipherivalgorithm-key-iv-options)
- [crypto.createDecipheriv](#cryptocreatedecipherivalgorithm-key-iv-options)

## crypto.createHash(algorithm[, options])

Creates and returns a hash object that can be used to generate hash digests using the given algorithm.

```typescript
import crypto from 'crypto';

const hash = crypto.createHash('sha256');

hash.update('some data to hash');

console.log(hash.digest('hex'));
// Prints: 6a2da20943931e9834fc12cfe5bb47bbd9ae43489a30726962b576f4e3993e50
```

## crypto.createCipher(algorithm, password[, options])

Creates and returns a Cipher object that uses the given algorithm and password.

```typescript
import crypto from 'crypto';

const cipher = crypto.createCipher('aes192', 'a password');

let encrypted = cipher.update('some clear text data', 'utf8', 'hex');

encrypted += cipher.final('hex');

console.log(encrypted);
```

## crypto.createCipheriv(algorithm, key, iv[, options])

Creates and returns a Cipher object that uses the given algorithm, key and initialization vector (iv).

```typescript
import crypto from 'crypto';

const DATA = 'mydata';
const ALGORITHM = 'aes-256-cbc';

const key = crypto.randomBytes(32);
const iv = crypto.randomBytes(16);

const cipher = crypto.createCipheriv(ALGORITHM, Buffer.from(key), iv);
let encrypted = cipher.update(DATA);
encrypted = Buffer.concat([encrypted, cipher.final()]);
console.log(encrypted.toString('hex'));
```

## crypto.createDecipheriv(algorithm, key, iv[, options])

Creates and returns a Decipher object that uses the given algorithm, key and initialization vector (iv).

```typescript
import crypto from 'crypto';

const DATA = 'mydata';
const ALGORITHM = 'aes-256-cbc';

const key = crypto.randomBytes(32);
const iv = crypto.randomBytes(16);

const cipher = crypto.createCipheriv(ALGORITHM, Buffer.from(key), iv);
let encrypted = cipher.update(DATA);
encrypted = Buffer.concat([encrypted, cipher.final()]);
console.log(encrypted.toString('hex'));

const decipher = crypto.createDecipheriv(ALGORITHM, Buffer.from(key), iv);
let decrypted = decipher.update(encrypted);
decrypted = Buffer.concat([decrypted, decipher.final()]);
console.log(decrypted.toString());
```





