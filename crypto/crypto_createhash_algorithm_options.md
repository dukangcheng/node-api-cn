<!-- YAML
added: v0.1.92
-->
- `algorithm` {string}
- `options` {Object} [`stream.transform` options][]
- Returns: {Hash}

Creates and returns a `Hash` object that can be used to generate hash digests
using the given `algorithm`. Optional `options` argument controls stream
behavior.

The `algorithm` is dependent on the available algorithms supported by the
version of OpenSSL on the platform. Examples are `'sha256'`, `'sha512'`, etc.
On recent releases of OpenSSL, `openssl list -digest-algorithms`
(`openssl list-message-digest-algorithms` for older versions of OpenSSL) will
display the available digest algorithms.

Example: generating the sha256 sum of a file

```js
const filename = process.argv[2];
const crypto = require('crypto');
const fs = require('fs');

const hash = crypto.createHash('sha256');

const input = fs.createReadStream(filename);
input.on('readable', () => {
  const data = input.read();
  if (data)
    hash.update(data);
  else {
    console.log(`${hash.digest('hex')} ${filename}`);
  }
});
```

