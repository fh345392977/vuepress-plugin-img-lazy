# vuepress-plugin-img-lazy

> a vuepress plugin to better supporting image lazy loading

**The plugin will preferentially use native image [lazy-loading](https://caniuse.com/#feat=loading-lazy-attr), if the browser does not support it, it will be implemented through lozad**

base on [markdown-it-img-lazy](https://github.com/tolking/markdown-it-img-lazy) and [markdown-it-imsize](https://github.com/tatsy/markdown-it-imsize) and [lozad](https://github.com/ApoorvSaxena/lozad.js)

[Live Demo and Documentation](https://tolking.github.io/vuepress-plugin-img-lazy/preview.html)

---

## Installation

``` sh
yarn add vuepress-plugin-img-lazy
# or
npm i vuepress-plugin-img-lazy
```

## Usage

``` js
module.exports = {
  plugins: [
    'img-lazy'
  ]
}
```

``` md
![img](/img.jpg)
# or
![img](/img.jpg =500x300) <!-- better -->
```

## Use in theme

- registered as global components

``` js
// enhanceAppFile.js
import ImgLazy from 'vuepress-plugin-img-lazy/ImgLazy'

export default ({ Vue }) => {
  Vue.component(ImgLazy.name, ImgLazy)
}
```

- or registered as components

``` js
import ImgLazy from 'vuepress-plugin-img-lazy/ImgLazy'

export default {
  components: { ImgLazy }
}
```

- use

``` vue
<template>
  <img-lazy src="/img.jpg" />
</template>
```

## Options

### useLoading
- Type: `Boolben`
- Default: `true`

Use the native image lazy-loading for the web

### selector
- Type: `string`
- Default: `lazy`

Default class name for image

## Other

1. [Base URL](https://vuepress.vuejs.org/guide/assets.html#rBase%20URL) already included by default, But it does not include the `<img/>` label in the markdown file <Badge text="^1.0.2"/>

If you need to use both `Base URL` and `<img/>` labels, refer to

``` md
<img :data-src="$withBase('/img.png')" loading="lazy" class="lazy">
```
