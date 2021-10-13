Anywhere 随启随用的静态文件服务器
==============================

Running static file server anywhere. 随时随地将你的当前目录变成一个静态文件服务器的根目录。

antwhere 全局命令替换为 preview

## 待做
替换 serve-index 提供的默认模板

## Installation

Install it as a command line tool via `npm -g`.

```sh
npm install anywhere -g
```

本地安装
```sh
npm link
```
本地卸载
```sh
npm uninstall -g preview
```
window 可在 C:\Users\<username>\AppData\Roaming\npm 下查看全局安装的包或者通过命令  npm list -g --dept 0

## Execution

```sh
$ preview
// or with port
$ preview -p 8000
// or start it but silent(don't open browser)
$ preview -s
// or with hostname
$ preview -h localhost -p 8888
// or with folder
$ preview -d ~/git/anywhere
// or enable html5 history
$ preview -f /index.html
```

## Help

```sh
$ preview --help
Usage:
  preview --help // print help information
  preview // 8000 as default port, current folder as root
  preview 8888 // 8888 as port
  preview -p 8989 // 8989 as port
  preview -s // don't open browser
  preview -h localhost // localhost as hostname
  preview -d /home // /home as root
  preview -f /index.html  // Enable html5 history,the index is /index.html
  preview --proxy http://localhost:7000/api // Support shorthand URL, webpack.config.js or customize config file
```

#### Proxy argvs

**Shorthand URL**
```
preview --proxy http://localhost:7000/api
                 \___________________/\___/
                              |         |
                           target    context
```
More about the [shorthand configuration](https://github.com/chimurai/http-proxy-middleware#shorthand).

**Webpack conofig**
```javascript
// webpack.conofig.js
module.exports = {
  devServer: {
    proxy: {
      '/api': {
        target: 'http://localhost:7000',
        changeOrigin: true
      }
    }
  }
}
```

**Customize config**
```javascript
// proxy.config.js
module.exports = {
  '/api': {
    target: 'http://localhost:7000',
    changeOrigin: true
  }
}
```
More proxy [http-proxy-middleware](https://github.com/chimurai/http-proxy-middleware#context-matching) help.

## Visit

```
http://localhost:8000
```
Automatically open default browser. 执行命令后，默认浏览器将为您自动打开主页。

## License
The MIT license.
