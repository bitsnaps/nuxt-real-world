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
# Deploy on Heroku

Login to heroku and create a new app with this configs:
```
heroku login
heroku create
heroku config:set NPM_CONFIG_PRODUCTION=false
heroku config:set HOST=0.0.0.0
heroku config:set NODE_ENV=production
```
then add to `package.json` the build script:
```
"heroku-postbuild":"npm run build"
```
and then create a `Procfile` in order to tell heroku how to build the app with this content:
```
web: npm run start
```
finally using git push the repo to `heroku` origin as follows:
```
git add -A
git commit -m "Configuration to deploy to heroku"
git push heroku master
```

P.S. Do to not forget to update dependencies whenever you get warnings:
```
npm update
```

Generate a static deployment
```
npm run generate
```
if you have a dynamic generated pages, you must add a dynamic routes config to `nuxt.config.js`, in this example:
File: nuxt.config.js
```
import EventService from './services/EventService.js'

export default {
  ...
  generate: {
    routes: () => {
      return EventService.getEvents().then(response => {
        return response.data.map(event => {
          return '/event/' + event.id
        })
      })
    }
  }  
}
```
you can then run a local web server to test (you could use http-server running `dist` directory):
```
http-server dist
```
