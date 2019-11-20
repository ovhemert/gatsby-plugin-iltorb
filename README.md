# gatsby-plugin-iltorb

[![Travis](https://img.shields.io/travis/com/ovhemert/gatsby-plugin-iltorb.svg?branch=master&logo=travis)](https://travis-ci.com/ovhemert/gatsby-plugin-iltorb)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/87a2946ec87e42869eb37cc731aee4e1)](https://www.codacy.com/app/ovhemert/gatsby-plugin-iltorb?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=ovhemert/gatsby-plugin-iltorb&amp;utm_campaign=Badge_Grade)
[![Known Vulnerabilities](https://snyk.io/test/npm/gatsby-plugin-iltorb/badge.svg)](https://snyk.io/test/npm/gatsby-plugin-iltorb)
[![Coverage Status](https://coveralls.io/repos/github/ovhemert/gatsby-plugin-iltorb/badge.svg?branch=master)](https://coveralls.io/github/ovhemert/gatsby-plugin-iltorb?branch=master)
[![Greenkeeper badge](https://badges.greenkeeper.io/ovhemert/gatsby-plugin-iltorb.svg)](https://greenkeeper.io/)
[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat)](http://standardjs.com/)

Gatsby plugin for preparing brotli-compressed versions of assets using iltorb native bindings.

*Note: This means that the plugin will try to download the binaries for your system. If it fails, it tries to build them using build tools that must already exist on the system. There is also a version of this plugin available, that does not use native bindings ([gatsby-plugin-brotli](https://github.com/ovhemert/gatsby-plugin-brotli/)). The difference is that compression takes a bit longer.*

```bash
/webpack-runtime-cde5506958f1afc4d89e.js
```
becomes
```bash
/webpack-runtime-cde5506958f1afc4d89e.js.br
```

## Requirements

This plugin will only generate the compressed files. To see them been served to the client, your Gatsby website should run on a production server that supports Brotli .br-files. The Gatsby development server **does not** serve the compressed versions.

## Installation

With npm:

```bash
npm install --save gatsby-plugin-iltorb
```

Or with Yarn:

```bash
yarn add gatsby-plugin-iltorb
```

## Usage

In your `gatsby-config.js` file add:

```javascript
module.exports = {
  plugins: [
    {
      resolve: 'gatsby-plugin-iltorb'
    }
  ]
}
```

By default, only `.css` and `.js` files are compressed, but you can override this with the `extensions` option.

```javascript
module.exports = {
  plugins: [
    {
      resolve: 'gatsby-plugin-iltorb',
      options: {
        extensions: ['css', 'html', 'js', 'svg']
      }
    }
  ]
}
```

You can even place all the brotli-compressed files (only the brotli ones, the uncompressed ones will
be saved in the `public` directory as usual) in a dedicated directory (ex. `public/brotli`):

```javascript
module.exports = {
  plugins: [
    {
      resolve: 'gatsby-plugin-iltorb',
      options: {
        path: 'brotli'
      }
    }
  ]
}
```

## Maintainers

Osmond van Hemert
[![Github](https://img.shields.io/badge/-website.svg?style=social&logoColor=333&logo=github)](https://github.com/ovhemert)
[![Web](https://img.shields.io/badge/-website.svg?style=social&logoColor=333&logo=nextdoor)](https://ovhemert.dev)

## Contributing

If you would like to help out with some code, check the [details](./docs/CONTRIBUTING.md).

Not a coder, but still want to support? Have a look at the options available to [donate](https://ovhemert.dev/donate).

## Sponsors

[![BrowserStack](./docs/assets/browserstack-logo.svg)](https://www.browserstack.com/)

## License

Licensed under [MIT](./LICENSE).

_NOTE: This plugin only generates output when run in `production` mode! To test, run: `gatsby build && gatsby serve`_
