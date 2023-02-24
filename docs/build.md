# 自行编译源码部署到任意web

**安装环境node**

下载源码解压后在目录中执行如下命令安装依赖，可能需要较长时间

```
npm install
```

**修改API路径**

位于/src/utils/requests.ts第8和第30行baseURL，可先进行修改后编译。

修改为自己的域名，后面的/client/v4 不要修改.

**构建前端**

```
npm run build
```

生成的文件在dist目录下

**部署页面**

上传dist目录下文件至网站

网站要求：

1、网站需要取消防跨站设置

2、注意网站需要添加如下反代设置

```
#添加请求头
add_header 'Access-Control-Allow-Origin' '*';
add_header 'Access-Control-Allow-Headers' '*';
add_header 'Access-Control-Allow-Methods' '*';
#反代配置
location /client/v4
{
    proxy_pass https://api.cloudflare.com;
    proxy_set_header Host api.cloudflare.com;
    proxy_ssl_server_name on;
    proxy_ssl_name api.cloudflare.com;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header REMOTE-HOST $remote_addr;
} 
```

