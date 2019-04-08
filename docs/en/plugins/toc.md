---
sidebarDepth: 3
---

# vuepress-plugin-toc <GitHubLink repo="vuepress/vuepress-plugin-toc"/>

`vuepress-plugin-toc` is a VuePress plugin for TOC (table of contents) component.

## Usage

### Global Installation

```bash
npm install -g vuepress-plugin-toc
# OR
yarn global add vuepress-plugin-toc
```

### Local Installation

```bash
npm install vuepress-plugin-toc
# OR
yarn add vuepress-plugin-toc
```

### Add to `config.js`

```js
module.exports = {
  plugins: [
    ['toc', {
      // level of headers to be included by default
      includeLevel: [2, Infinity],
      // disable markdown syntax (you can still use <TOC> component)
      markerPattern: false,
    }],
  ],
}
```
or
```js
module.exports = {
  plugins: {
    toc: {
      // custom container class
      containerClass: 'toc',
      // i18n header html
      headerHtml: {
        '/zh/': '<p><strong>目录</strong></p>',
        '/en/': '<p><strong>Contents</strong></p>',
      },
    },
  },
}
```

## TOC Component

- **props:** `listType`, `includeLevel`
- **slots:** `header`, `footer`

### Demonstration

**Input:**

```md
<TOC :list-type="['ol', 'ul']">
  <p slot="header"><strong>Custom Table of Contents</strong></p>
</TOC>
```

**Output:**

<TOC :list-type="['ol', 'ul']">
  <p slot="header"><strong>Custom Table of Contents</strong></p>
</TOC>

## Configurations

### includeLevel

- **type:** `[number, number?]`
- **default:** `[2, 3]`

Specify which level of headers should be included. The default value for the second number will be `Infinity`.

### containerClass

- **type:** `string`
- **default:** `'table-of-contents'`

Class name(s) for TOC container.

### markerPattern

- **type:** `RegExp | false`
- **default:** `/^\[\[toc\]\]/im`

The regular expression for the marker to be replaced with TOC. Setting to `false` will disable the markdown syntax (you can still use the `<TOC/>` component).

### listType

- **type:** `string | string[]`
- **default:** `'ul'`

The tags of lists. If specified as an array, the component will take the first element as the first-level list type and so on. If there are not enough values provided, the last value will be used for all the remaining list types.

### headerHtml

- **type:** `string | Record<string, string>`
- **default:** `''`

An HTML string to be inserted at the top of TOC container. If an object was specified, it will depend on current locale.

### footerHtml

- **type:** `string | Record<string, string>`
- **default:** `''`

An HTML string to be inserted at the bottom of TOC container. If an object was specified, it will depend on current locale.
