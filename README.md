# Dnsflare

可视化的修改 Cloudflare Zone 的解析地址，已修改适应于自行编译部署到自己的Web中。开发者源码地址请访问 [5aaee9/Dnsflare](https://github.com/5aaee9/Dnsflare)


## 原因
Cloudflare 非常鸡贼的 ban 掉了 `externallyManaged` 用户访问 Cloudflare 控制台编辑 DNS Record 的功能, 然后 Partner 已经凉凉, 但是又眼馋 pro

### 优点
所有请求由本地浏览器产生, 服务端仅进行 CORS 处理

Partner 无法直接添加 A 记录 (据说), 而且 Partner API 在开启 2FA 的情况下无法使用，Dnsflare不受影响

## 使用
到 [Cloudflare 的 API Token 设定](https://dash.cloudflare.com/profile/api-tokens) 中新建一个 Token, 给这个 Token 如下权限

- Zone.DNS （域.DNS）                                                编辑权限 (用于写入 DNS 记录)
- Zone.Zone（域.域）                                                    读取权限 (用于读取域名列表)

- Zone.SSL and Certificates（域.SSL和证书）            编辑权限 (用于展示和修改 SSL 证书供应商)

## 部署
[使用 Cloudflare Pages 部署](docs/deploy_cloudflare.md)

[自行编译部署](docs/build.md)

下载[Releases](https://github.com/fcurrk/Dnsflare/releases)部署：下载源码上传Web，取消防跨站及开启反代具体方法见[自行编译部署](docs/build.md)部分内容

## License
Open sourced under the MIT license.
