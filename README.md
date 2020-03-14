# real-world-nuxt

> My brilliant Nuxt.js project

## Build Setup

``` bash
# install dependencies
$ npm install

# serve with hot reload at localhost:3000
$ npm run dev

# build for production and launch server
$ npm run build
$ npm run start

# generate static project
$ npm run generate
```

For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).

if you didn't select Axios when creating nuxt app, you can install axios using npm:
```
npm install @nuxtjs/axios
```
Then in `nuxt.config.js`:
```
module.exports = {
  modules: ['@nuxtjs/axios'],
}
```

If you want to run nuxt in a different port:
```
set PORT=3001
npm run dev
```
If you want to run json-server with a delay (in order to test the progress bar for example):
```
json-server --watch db.json --delay 2000
```
