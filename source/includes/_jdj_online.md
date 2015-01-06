# 金豆荚上线文档

## 上线环境

### 生产环境服务器

![阿里云服务](./ali_servers.jpg)

## 上线操作步骤

<<<<<<< HEAD
### nginx的配置 （吴杭军请你补充这个模块的内容）

  * https配置
    1. 创建文件夹 /etc/nginx/cert ,上传自签名证书和key到该目录。
    2. 新建 /etc/nging/conf.d/ssl.conf 文件

``` 
#ssl.conf
=======
1. nginx的配置 （吴杭军请你补充这个模块的内容）
	* https配置：
	i.创建文件夹 /etc/nginx/cert ,上传自签名证书和key到该目录。
	ii.新建 /etc/nging/conf.d/ssl.conf 文件:
#Nginx https server

```
>>>>>>> 6baff696ea01de2b3859f2cbd0848960de96d99f
server {
listen       443 ssl;
server_name  localhost;
charset utf-8;
access_log /var/log/nginx/ssl.access.log main;

   ssl  on;
   ssl_certificate  cert/sunlights.crt;
   ssl_certificate_key  cert/sunlights.key;
   ssl_session_cache  shared:SSL:10m;
   ssl_session_timeout  15m;
   ssl_protocols SSLv2 TLSv1 TLSv1.1 TLSv1.2;
   ssl_ciphers  HIGH:!aNULL:!MD5;
   ssl_prefer_server_ciphers  on;

location / {
       root   /data;
       index  index.html index.htm;
   }

location /api/ {
        proxy_pass http://192.168.0.97:9001/;
        proxy_http_version 1.1;
        proxy_set_header Connection "";
        proxy_redirect off;
        proxy_set_header HOST $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        client_max_body_size 10m;
        client_body_buffer_size 128k;
        proxy_connect_timeout 90;
        proxy_send_timeout 90;
        proxy_read_timeout 90; 
        proxy_buffer_size 8k; 
        proxy_buffers 4 32k; 
        proxy_busy_buffers_size 64k;
        reset_timedout_connection on;
   }

location /api_dev/ {
        proxy_pass http://192.168.0.95:9005/;
        proxy_http_version 1.1;
        proxy_set_header Connection "";
        proxy_redirect off;
        proxy_set_header HOST $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        client_max_body_size 10m;
        client_body_buffer_size 128k;
        proxy_connect_timeout 90;
        proxy_send_timeout 90;
        proxy_read_timeout 90; 
        proxy_buffer_size 8k; 
        proxy_buffers 4 32k; 
        proxy_busy_buffers_size 64k;
        reset_timedout_connection on;
   }
}
```

  * 负载均衡配置
  * H5静态资源配置
	
### postgresql放在pgDB-XXX上（吴杭军请你补充这个模块的内容）
	* 进行Master-Slave配置
	* 初始化数据导入
	
### OP部署在ngix-http服务器上  (jekins的截图请『老汤同学弄一下， 图片的宽度请保存为1024px 』)
	* 通过jekins任务一键部署 （把jekins上的这个任务的截图放到images目录下）
	* OP访问URL

### ThirdPartService部署到ngix-http服务器上（把jekins上的这个任务的截图放到images目录下）
    
  * ThirdPartService的功能介绍
	
### FP部署在finplat-1服务器上
    
  * 通过jekins任务一键部署（把jekins上的这个任务的截图放到images目录下）
  * FP访问URL
    




