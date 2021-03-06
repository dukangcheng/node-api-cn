<!-- YAML
added: v10.0.0
-->

* `prefix` {string}
* `options` {string|Object}
  * `encoding` {string} **Default:** `'utf8'`
* Returns: {Promise}

Creates a unique temporary directory and resolves the `Promise` with the created
folder path. A unique directory name is generated by appending six random
characters to the end of the provided `prefix`.

The optional `options` argument can be a string specifying an encoding, or an
object with an `encoding` property specifying the character encoding to use.

```js
fsPromises.mkdtemp(path.join(os.tmpdir(), 'foo-'))
  .catch(console.error);
```

The `fsPromises.mkdtemp()` method will append the six randomly selected
characters directly to the `prefix` string. For instance, given a directory
`/tmp`, if the intention is to create a temporary directory *within* `/tmp`, the
`prefix` must end with a trailing platform-specific path separator
(`require('path').sep`).

