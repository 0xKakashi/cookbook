![0xKakashi](./banner.png)

# 📔 COOKBOOK

> Developer Bookmarks, Resources, References and Guides

---

## CONFIGURATION

> Configuration and Settings Templates

* [`package.json`](#package.json)
* [`.gitignore`](#gitignore)

---

### `package.json`

```js
{
  "name": "app",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "directories": {
    "doc": "doc",
    "lib": "lib",
    "test": "test
  },
  "scripts": {
    "test": "echo \"testing...\"",
    "
  },
  "repository": {
    "type": "git",
    "url": "git+https://github.com/0xKakashi/app.git"
  },
  "keywords": [],
  "author": "Kakashi <kakashi.crypto@protonmail.com>",
  "license": "ISC",
  "homepage": "https://github.com/0xKakashi/app#readme"
}
```

---

### `.gitignore`

```
# environment
.env
.env.dev
.env.development
.env.staging
.env.prod
.env.production

# ide
.idea

# modules
node_modules/
jspm_packages/
bower_components
sw.*

# frameworks
.next
.nuxt
dist
.vuepress/dist
.serverless

# compilation
artifacts
.artifacts
cache
.cache
tmp
.tmp
build
.build
build/Release
coverage
.coverage
typings

# outputs
.nyc_output
.grunt
.npm
.eslintcache
.node_repl_history
.yarn-integrity

# logs
logs
*.log
npm-debug.log*
yarn-debug.log*
yarn-error.log*

# runtime
pids
*.pid
*.seed
*.pid.loc
```
