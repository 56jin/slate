﻿# 金豆荚上线文档

postgresql放在pgDB-XXX上（By hangjun.wu@sunlinghts.cc）

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

### 配置OP上的conf/prod.conf
    ![配置OP上的conf/prod.conf](./op_prod_conf1.png)
    ![配置OP上的conf/prod.conf](./op_prod_conf2.png)

### 将master上最新代码merge到test上，test上稳定运行并测试通过，将test上的稳定代码merge到release上

### 通过jekins任务一键部署 （把jekins上的这个任务的截图放到images目录下）
  * jekins上项目名称为op-prd
  * jekins资源管理上的配置
  ![jekins资源管理上的配置](./op-prd-resourceMng.png)
  * jekins构建的配置
  ![jekins构建的配置](./op-prd-build.png)
  * jekins上构建后的操作配置
  ![jekins上构建后的操作配置](./op-prd-opafterbuild.png)
  * 配置完以上的步骤后，点击项目op-prd上的立即构建，看Console上的日志输出

### OP访问http://121.40.204.123:9006

### 配置金豆荚系统数据
  * 产品管理配置：需要配置的是产品信息、基金信息
  
    1.添加“数米”供应商
    
    ![添加供应商](./add_suppler.png)
    
    2.基金代码同步
    
    ![基金代码同步](./grab_fund_code.png)
    
    3.添加产品
    
    ![添加产品](./add_product.png)
    
    4.同步所有需要同步的基金基础信息
    
    ![同步基金](./grab_fund.png)
    
    5.同步所有产品的历史收益
    
    ![同步历史收益](./grab_profit_history.png)
    
    6.添加定时器
        
    + 基金基础数据同步任务,每天早上8点执行
    ![基金基础数据同步任务](./fund_job.png)
    
    + 基金历史收益同步任务，每5分钟执行
    ![基金历史收益同步任务](./fund_profit_history_job.png)
    
    + 基金历史收益监控任务，每小时执行
    ![基金历史收益监控任务](./fund_profit_obtain.png)
    
    + 基金档案同步任务，每天24点执行
    ![基金档案同步任务](./fund_archive.png)
    

  * 活动管理配置：需要配置的是活动场景、奖励类型、分享信息、活动列表、兑换场景、活动错误信息维护
  
  
  

### ThirdPartService部署到ngix-http服务器上（把jekins上的这个任务的截图放到images目录下）

### 配置ThirdPartService上的conf/prod.conf
  
  ![配置ThirdPartService上的conf/prod.conf](./3party_prod_conf.png)

### 将master上最新代码merge到test上，test上稳定运行并测试通过，将test上的稳定代码merge到release上

### 通过jekins任务一键部署 （把jekins上的这个任务的截图放到images目录下）
  * jekins上项目名称为3party-prd
  * jekins资源管理上的配置
  ![jekins资源管理上的配置](./3party-prd-resourceMng.png)
  * jekins构建的配置
  ![jekins构建的配置](./3party-prd-build.png)
  * jekins上构建后的操作配置
  ![jekins上构建后的操作配置](./3party-prd-opafterbuild.png)
  * 配置完以上的步骤后，点击项目3party-prd上的立即构建，看Console上的日志输出

### ThirdPartService的功能介绍
  * 发送短信
  * 推送消息
  * 获取短URL

	
### FP部署在finplat-1服务器上

### 配置FP上的conf/prod.conf
  ![配置FP上的conf/prod.conf](./fp_prod_conf.png)


### 将master上最新代码merge到test上，test上稳定运行并测试通过，将test上的稳定代码merge到release上

### 通过jekins任务一键部署 （把jekins上的这个任务的截图放到images目录下）
	* jekins上项目名称为fp-prd
	* jekins资源管理上的配置
	![jekins资源管理上的配置](./fp-prd-resourceMng.png)
	* jekins构建的配置
	![jekins构建的配置](./fp-prd-build.png)
	* jekins上构建后的操作配置
	![jekins上构建后的操作配置](./fp-prd-opafterbuild.png)
	* 配置完以上的步骤后，点击项目fp-prd上的立即构建，看Console上的日志输出
### 通过jekins任务一键部署（把jekins上的这个任务的截图放到images目录下）

### FP访问URL
    




