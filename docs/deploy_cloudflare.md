# 部署到 Cloudflare

请使用[5aaee9/Dnsflare](https://github.com/5aaee9/Dnsflare)源部署

安装 wrangler cli:

```
npm i -g wrangler
```

构建前端页面

```
yarn install
yarn run build
```

部署页面

```
wrangler pages publish dist
```
