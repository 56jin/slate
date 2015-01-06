# 金豆荚上线文档

## 上线环境

### 生产环境服务器

![阿里云服务](./ali_servers.jpg)

## 上线操作步骤

1. nginx的配置 （吴杭军请你补充这个模块的内容）
	* 需要进行https配置
	* 负载均衡配置
	* H5静态资源配置
	
2. postgresql放在pgDB-XXX上（吴杭军请你补充这个模块的内容）
	* 进行Master-Slave配置
	* 初始化数据导入
	
3. OP部署在ngix-http服务器上  (jekins的截图请『老汤同学弄一下， 图片的宽度请保存为1024px 』)
	* 通过jekins任务一键部署 （把jekins上的这个任务的截图放到images目录下）
	* OP访问URL

4. ThirdPartService部署到ngix-http服务器上（把jekins上的这个任务的截图放到images目录下）
    * ThirdPartService的功能介绍
	
5. FP部署在finplat-1服务器上
    * 通过jekins任务一键部署（把jekins上的这个任务的截图放到images目录下）
    * FP访问URL
    




