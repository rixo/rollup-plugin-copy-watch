# rollup-plugin-copy-watch

A fork of [rollup-plugin-copy](https://github.com/vladshcherbin/rollup-plugin-copy) with an additional `watch` to watch other sources than just Rollup's bundle content (e.g. your static assets directory).

[![Build Status](https://travis-ci.org/vladshcherbin/rollup-plugin-copy.svg?branch=master)](https://travis-ci.org/vladshcherbin/rollup-plugin-copy)
[![Codecov](https://codecov.io/gh/vladshcherbin/rollup-plugin-copy/branch/master/graph/badge.svg)](https://codecov.io/gh/vladshcherbin/rollup-plugin-copy)

Copy files and folders, with glob support.

## Installation

```bash
# yarn
yarn add rollup-plugin-copy-watch -D

# npm
npm install rollup-plugin-copy-watch -D
```

## Usage

```js
// rollup.config.js
import copy from 'rollup-plugin-copy-watch'

export default {
  input: 'src/index.js',
  output: {
    file: 'dist/app.js',
    format: 'cjs'
  },
  plugins: [
    copy({
      // the watch option is passed directly to Chokidar, so it can be a file,
      // dir, array or glob(s)
      watch: 'static',

      targets: [
        { src: 'src/index.html', dest: 'dist/public' },
        { src: ['assets/fonts/arial.woff', 'assets/fonts/arial.woff2'], dest: 'dist/public/fonts' },
        { src: 'assets/images/**/*', dest: 'dist/public/images' }
      ]
    })
  ]
}
```

### Configuration

The configuration is exactly the same as [rollup-plugin-copy](https://github.com/vladshcherbin/rollup-plugin-copy#configuration), with just one option added. Refer to the original plugin for all other options.

#### watch

Type: `string|string[]` Default: `null`

Paths to files, dirs to be watched recursively, or glob patterns.

This is passed directly to [`chokidar.watch`](https://github.com/paulmillr/chokidar#api).

## Original Author

`rollup-plugin-copy`: [Cédric Meuter](https://github.com/meuter)

## License

MIT
