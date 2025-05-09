# Lodash

A modern JavaScript utility library delivering modularity, performance & extras.

examples

## “Array” Methods


`_.chunk(array, [size=1])`

Creates an array of elements split into groups the length of size. If array can't be split evenly, the final chunk will be the remaining elements.


## how to import lodash

Q:

if you have two variants of import:

```
import { has } from 'lodash'
import has from 'lodash/has'
```

A:

`import has from 'lodash/has';`

cause is better because lodash holds all its functions in a single file, so rather than import the whole 'lodash' library at 100k, it's better to just import lodash's has function which is maybe 2k.

If you are using webpack 4, the following code is tree shakable.

`import { has } from 'lodash-es';`

The points to note;

1. CommonJS modules are not tree shakable so you should definitely use lodash-es, which is the Lodash library exported as ES Modules, rather than lodash (CommonJS).
2. lodash-es's package.json contains "sideEffects": false, which notifies webpack 4 that all the files inside the package are side effect free (see https://webpack.js.org/guides/tree-shaking/#mark-the-file-as-side-effect-free).
3. This information is crucial for tree shaking since module bundlers do not tree shake files which possibly contain side effects even if their exported members are not used in anywhere.

As of version 1.9.0, Parcel also supports "sideEffects": false, threrefore `import { has } from 'lodash-es';` is also tree shakable with Parcel. It also supports tree shaking CommonJS modules, though it is likely tree shaking of ES Modules is more efficient than CommonJS. [example](https://github.com/kimamula/tree-shaking-demo)