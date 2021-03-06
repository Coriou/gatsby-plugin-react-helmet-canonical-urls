# gatsby-plugin-react-helmet-canonical-urls

This can be use as a drop in replacement of [`gatsby-plugin-canonical-urls`](https://www.npmjs.com/package/gatsby-plugin-canonical-urls).

Add canonical links to HTML pages Gatsby generates using react helmet.

This implementation is primarily helpful for distinguishing between https/http,
www/no-www but could possibly be extended to help with when sites add multiple
paths to the same page.

## Motivation

`gatsby-plugin-canonical-urls` and `gatsby-plugin-react-helmet` are plugins that do not always play well together.
The first one always inserts a default canonical url, but doesn't allow to override that value in an easy way.
When trying to use react helmet to override `gatsby-plugin-canonical-urls` default url, you will end up with
two canonical tags.

This plugin, as writes the default canonical url using react helmet, allows to override default canonical url just
using the standard react helmet api.

## Install

`npm install --save gatsby-plugin-react-helmet gatsby-plugin-react-helmet-canonical-urls`

## How to use

```javascript
// In your gatsby-config.js
plugins: [
  `gatsby-plugin-react-helmet`,
  {
    resolve: `gatsby-plugin-react-helmet-canonical-urls`,
    options: {
      siteUrl: `https://www.example.com`,
    },
  },
]
```

With the above configuration, the plugin will add to the head of every HTML page
a `rel=canonical` e.g.

```html
<link rel="canonical" href="http://www.example.com/about-us/" />
```
