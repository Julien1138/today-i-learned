# Fetch API on port 80 while serving on port 8080
While in development, I use the `npm run serve` command to serve my frontend. It is served on port 8080, so when fetching the backend if was sending requests to `http://localhost:8080/api/...` instead of `http://localhost/api/...`.

The solution is to configure vue to proxy requests that do not match a static file to an other url :
```js
module.exports = {
  devServer: {
    proxy: {
      '^/api': {
        target: 'http://localhost:80',
        ws: true,
        changeOrigin: true,
      },
    },
  },
}
```
The `changeOrigin` parameter is needed for CORS backend policy.

[reference](https://cli.vuejs.org/config/#devserver-proxy)
