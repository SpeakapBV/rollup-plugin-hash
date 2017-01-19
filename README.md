# rollup-plugin-hash [![Travis Build Status][travis-img]][travis]

[travis-img]: https://travis-ci.org/phamann/rollup-plugin-hash.svg
[travis]: https://travis-ci.org/phamann/rollup-plugin-hash
[rollup]: https://github.com/rollup/rollup

[Rollup] plugin to compose bundle output filenames with unique hashes, to facilitate long-term caching of your static resources.

It uses is simple place holder pattern to substitue filename with bundle hash. I.e.
`main.[hash].js`
becomes:
`main.07d2bf0d12655d9f51c0637718da4889.js`

## Install

Via npm
```sh
npm install --save-dev rollup-plugin-hash
```

Via yarn
```sh
yarn add --dev rollup-plugin-hash
```

## Usage

```js
import { rollup } from 'rollup';
import hash from 'rollup-plugin-hash';

rollup({
    entry: 'main.js',
    plugins: [
        hash({ 
			dest: 'main.[hash].js'	
		})
    ]
});
```


## Options

### dest

Type: `string`
Required: `true`

The template of your filename destination. Must include the placeholder `[hash]` to be replaced.

### replace

Type: `boolean`
Default: `false`
Required: `false`

Whether the hashed version should replace the main output file generated by Rollup. 
Useful in CI environments where you don't need any none rev'd files.

### algorithm

Type: `string`
Default: `sha1`
Required: `true`

Hashing algorithm used to generate hash. Can be one of `md5`, `sha1`, `sha256`, `sha512`

# License

MIT ©
