---
sidebarDepth: 3
---

# vuepress-plugin-toc <GitHubLink repo="vuepress/vuepress-plugin-toc"/>

`vuepress-plugin-toc` 是一个渲染目录的 VuePress 插件。

## 用法

### 全局安装

```bash
npm install -g vuepress-plugin-toc
# 或者
yarn global add vuepress-plugin-toc
```

### 局部安装

```bash
npm install vuepress-plugin-toc
# 或者
yarn add vuepress-plugin-toc
```

### 添加到 `config.js`

```js
module.exports = {
  plugins: [
    ['toc', {
      // 默认包含的标题级别
      includeLevel: [2, Infinity],
      // 禁用 markdown 语法 (你仍然可以使用 <TOC> 组件)
      markerPattern: false,
    }],
  ],
}
```
或者
```js
module.exports = {
  plugins: {
    toc: {
      // 定制容器类名
      containerClass: 'toc',
      // 多语言目录标题
      headerHtml: {
        '/zh/': '<p><strong>目录</strong></p>',
        '/en/': '<p><strong>Contents</strong></p>',
      },
    },
  },
}
```

## TOC 组件

- **props:** `listType`, `includeLevel`
- **slots:** `header`, `footer`

### 示例

**输入:**

```md
<TOC :list-type="['ol', 'ul']">
  <p slot="header"><strong>自定义目录</strong></p>
</TOC>
```

**输出:**

<TOC :list-type="['ol', 'ul']">
  <p slot="header"><strong>自定义目录</strong></p>
</TOC>

## 配置

### includeLevel

- **类型:** `[number, number?]`
- **默认值:** `[2, 3]`

决定哪些级别的标题会被显示在目录中。第二个参数的默认值为 `Infinity`。

### containerClass

- **类型:** `string`
- **默认值:** `'table-of-contents'`

设置目录容器的类名。

### markerPattern

- **类型:** `RegExp | false`
- **默认值:** `/^\[\[toc\]\]/im`

标题匹配的正则表达式。如果设为 `false`，会禁用 markdown 语法（不过你仍然可以使用 `<TOC>` 组件）。

### listType

- **类型:** `string | string[]`
- **默认值:** `'ul'`

各级列表的标签。如果设置为了数组，组件将会使用第一个元素作为第一级列表的标签，以此类推。如果提供的标签不够多，将使用提供的最后一个值作为全部剩下的列表标签。

### headerHtml

- **类型:** `string | Record<string, string>`
- **默认值:** `''`

在目录开头插入的 HTML 字符串。如果提供的是一个对象，默认标题将会基于当前 locale 选取。

### footerHtml

- **类型:** `string | Record<string, string>`
- **默认值:** `''`

在目录结尾插入的 HTML 字符串。如果提供的是一个对象，默认标题将会基于当前 locale 选取。
