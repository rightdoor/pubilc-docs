---
title: 关于Mathjax字体加载问题
description: 解决Mathjax字体加载问题
created: 2026-03-11 23:23:12
updated: 2026-03-11 23:23:12
id: 7ghj88j1
---

## 网络问题

部分地区因网络问题而无法加载字体，导致页面显示空白且无法正常显示，下面是几种解决办法。

### 使用本地字体（默认）

下载字体并引用，然后在构建时复制到`dist`文件夹。这样导致构建文件夹高达`14mb`，字体文件就占了`65%`，这是迫不得已的办法。

安装字体包：

```bash
pnpm install @mathjax/mathjax-tex-font
```

修改配置文件`src/main/index.ts`：

```ts
...
w.MathJax = {
  loader: {
    paths: {
      mathjax: '/mathjax',
      // 字体文件路径
      fonts: '/mathjax-fonts',
    },
...
  // 设置输出字体
  output: {
    font: 'mathjax-tex',
  },
}
...
```

构建命令不变，已经预设命令复制字体`mathjax-tex`文件到`dist`：

```bash
pnpm run build
```

需要其他字体请自行修改。

### 使用其他CDN

根据官方文档 <https://docs.mathjax.org/en/latest/output/fonts.html#font-extensions> 所写，可以设置为其他CDN调用的形式。

参考：

```ts
...
w.MathJax = {
  loader: {
    paths: {
      mathjax: '/mathjax',
      // 不使用字体文件路径
      //fonts: '/mathjax-fonts',
    },
...
  // 设置输出字体指向CDN地址
  output: {
    font: 'https://cdn.jsdelivr.net/npm/@mathjax/mathjax-tex-font',
  },
}
...
```

官方默认使用`jsDelivr`，请修改到其他访问速度快的CDN网站。

构建使用不同的命令，该命令不包含复制字体文件代码：

```bash
pnpm run build-origin
```

### 命令对比

build-origin：`vue-tsc -b && vite build`

build：`vue-tsc -b && vite build && node -e \"const fs=require('node:fs');const path=require('node:path');const src=path.dirname(require.resolve('@mathjax/mathjax-tex-font/package.json'));const dst=path.join('dist','mathjax-fonts','mathjax-tex-font');fs.rmSync(dst,{recursive:true,force:true});fs.mkdirSync(path.dirname(dst),{recursive:true});fs.cpSync(src,dst,{recursive:true});\"`
