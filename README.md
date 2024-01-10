# soip
const http = require('http');
const httpProxy = require('http-proxy');

const targetUrl = 'http://target-url.com';

const server = http.createServer((req, res) => {
  const { url } = req;

  httpProxy.web(req, res, {
    target: targetUrl,
    changeOrigin: true,
    pathRewrite: { '^/proxy': '' }
  });
});

server.listen(8080, () => {
  console.log('Proxy server listening on port 8080');
});
