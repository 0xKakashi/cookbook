![0xKakashi](../banner.png)

# 📔 COOKBOOK

> Developer Bookmarks, Resources, References and Guides

---

## NUXT.JS

> Nuxt.js Frontend UI Framework Templates

[Documentation](https://nuxtjs.org) | [GitHub](https://github.com/nuxt/nuxt.js) | [NPM](https://npmjs.com/package/nuxt)

---

* [Configuration](#configuration)
* [Layouts](#layouts)
* [Pages](#pages)
* [Plugins](#plugins)
* [Store](#store)

---

### CONFIGURATION

```js
require('dotenv').config();

export default {
  head: {},
  css: [],
  loading: {},
  loadingIndicator: {},
  modules: [],
  plugins: [],
  build: {}
}
```

---

### LAYOUTS

__Default__

```vue
<template>
  <div id="main">
    <nuxt />
  </div>
</template>

<script>
export default {}
</script>

<style lang="postcss" scoped>
#main {}
</style>
```

__Error__

```vue
<template>
  <section id="error">
    <h1>Error</h1>
  </section>
</template>

<script>
export default {
  props: {
    error: {
      type: Object,
      required: true
    }
  }
}
</script>

<style lang="postcss" scoped>
section#error {}
</style>
```

---

### PAGES

__Default__

```vue
<template>
  <section>
    <h1>Index</h1>
  </section>
</template>

<script>
export default {}
</script>

<style lang="postcss" scoped>
</style>
```

---

### PLUGINS

__Default__

```js
export default (context, inject) => {
  inject('myFunc', ({ store }) => {
    return store.getters.getData
  });
}
```

---

### STORE

__State__

```js
/**
 * @module
 * @name   state
 * @desc   nuxt.js vuex store - state management
 */
export default () => ({
  data: {}
})
```

__Actions__

```js
/**
 * @module
 * @name   actions
 * @desc   nuxt.js vuex store - state actions
 */
export default {
  initialize: async function() {}
}
```

__Mutations__

```js
export default {
  ADD_DATA: (state, payload) => {
    state.data.push(payload)
  }
}
```

__Getters__

```js
export default {
  getData: async function(state) {
    return state.data
  }
}
```
