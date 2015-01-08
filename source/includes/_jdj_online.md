# 金豆荚上线文档

## 上线环境

### 生产环境服务器

![阿里云服务](./ali_servers.jpg)

## 上线操作步骤

1. nginx的配置 （By hangjun.wu@sunlinghts.cc）
	* https配置：

	i.创建文件夹 /etc/nginx/cert ,上传自签名证书和key到该目录

	ii.新建 /etc/nging/conf.d/ssl.conf 文件:



server {
      listen 443 ssl;
      server_name localhost;
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

	* 负载均衡配置

	* H5静态资源配置

	
2. postgresql放在pgDB-XXX上（By hangjun.wu@sunlinghts.cc）

	* Master-Slave配置

	 i.新建用户rep_user，并赋予replication权限：CREATE USER rep_user REPLICATION LOGIN CONNECTION LIMIT 4;

	 ii.修改 postgresql.conf 文件：

            wal_level = hot_standby

            archive_mode = on

            archive_command = 'cp %p  /db/pg_archive/%f  < /dev/null'  //本地路径归档

	 iii.编辑 pg_hba.conf 文件：

	    host   replication   rep_user 10.251.236.185/32   trust    //slave的IP地址

	 iv.在slave服务器上执行初始化数据：

	    pg_basebackup -D /var/lib/pgsql/9.3/data -Fp -Xs -v -P -h 172.16.1.74 -p 5432 -U rep_user 
//使用 pg_basebackup 从主库生成备库


	
### OP部署在ngix-http服务器上  (jekins的截图请『老汤同学弄一下， 图片的宽度请保存为1024px 』)

    * 配置OP上的conf/prod.conf
    ![配置OP上的conf/prod.conf](./op_prod_conf1.png)
    ![配置OP上的conf/prod.conf](./op_prod_conf2.png)

    * 将master上最新代码merge到test上，test上稳定运行并测试通过，将test上的稳定代码merge到release上

	* 通过jekins任务一键部署 （把jekins上的这个任务的截图放到images目录下）
        1：jekins上项目名称为op-prd
        2：jekins资源管理上的配置
        ![jekins资源管理上的配置](./op-prd-resourceMng.png)
        3：jekins构建的配置
        ![jekins构建的配置](./op-prd-build.png)
        4：jekins上构建后的操作配置
        ![jekins上构建后的操作配置](./op-prd-opafterbuild.png)
        5：配置完以上的步骤后，点击项目op-prd上的立即构建，看Console上的日志输出

	* OP访问http://121.40.204.123:9006

	* 配置金豆荚系统数据
    1：产品管理配置：需要配置的是产品信息、基金信息

    2：活动管理配置：需要配置的是活动场景、奖励类型、分享信息、活动列表、兑换场景、活动错误信息维护


### ThirdPartService部署到ngix-http服务器上（把jekins上的这个任务的截图放到images目录下）
  * 配置ThirdPartService上的conf/prod.conf
        ![配置ThirdPartService上的conf/prod.conf](./3party_prod_conf.png)

  * 将master上最新代码merge到test上，test上稳定运行并测试通过，将test上的稳定代码merge到release上

  * 通过jekins任务一键部署 （把jekins上的这个任务的截图放到images目录下）
        1：jekins上项目名称为3party-prd
        2：jekins资源管理上的配置
        ![jekins资源管理上的配置](./3party-prd-resourceMng.png)
        3：jekins构建的配置
        ![jekins构建的配置](./3party-prd-build.png)
        4：jekins上构建后的操作配置
        ![jekins上构建后的操作配置](./3party-prd-opafterbuild.png)
        5：配置完以上的步骤后，点击项目3party-prd上的立即构建，看Console上的日志输出
  * ThirdPartService的功能介绍
        1:发送短信
        2：推送消息
        3：获取短URL

	
### FP部署在finplat-1服务器上
  * 配置FP上的conf/prod.conf
      ![配置FP上的conf/prod.conf](./fp_prod_conf.png)


  * 将master上最新代码merge到test上，test上稳定运行并测试通过，将test上的稳定代码merge到release上

  * 通过jekins任务一键部署 （把jekins上的这个任务的截图放到images目录下）
  	1：jekins上项目名称为fp-prd
  	2：jekins资源管理上的配置
  	![jekins资源管理上的配置](./fp-prd-resourceMng.png)
  	3：jekins构建的配置
  	![jekins构建的配置](./fp-prd-build.png)
  	4：jekins上构建后的操作配置
  	![jekins上构建后的操作配置](./fp-prd-opafterbuild.png)
  	5：配置完以上的步骤后，点击项目fp-prd上的立即构建，看Console上的日志输出
  * 通过jekins任务一键部署（把jekins上的这个任务的截图放到images目录下）
  * FP访问URL
    




