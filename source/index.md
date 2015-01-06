---
title: API Reference

language_tabs:
  - java
  - objective-C
  - javascript

includes:
  - jdj_online
  - common
  - core
  - account
  - customer
  - trade
  - errors
  - angularjs_style_guide

search: false
---

# 使用介绍

请大家把自己负责模块的API文档写到includes目录下对应的makedown文件里面。
具体的写法请参考demo.md文件。
## hosts

[Git 简单使用指南](http://www.bootcss.com/p/git-guide/)

### windows

在`C:\Windows\System32\drivers\etc\hosts`添加下面服务器的信息

### mac

在`\etc\hosts`添加下面服务器的信息

```
192.168.0.97 SATURN
192.168.0.96 EARTH
192.168.0.95 MARS
192.168.0.94 VENUS
```

## server




主机名	        | 描述	        | RAM	 | ROM	 | IP	            | 用户名	    | 密码	      | 服务
---------       | -----------   | ------ | ----- | -----------------|-----------|-------      | ----------- 
SH-YIYUE-V001	|kvm宿主机	    |	     |	     |192.168.0.99	    |root	    |ZSE4RFVGY70-=|	
				|	            |        |       |                  |admin	    |zse4rfvgy7	  |
SATURN	        |测试服务器	    |10G	 |40G	 |192.168.0.97	    |root	    |zse4rfvgy7,./|[Nexus](http://saturn:8081/nexus) (admin/admin123)	
				|	            |        |       |                  |admin	    |zse4rfvgy7	  |[Jenkins](http://saturn:8080) deprecated
				|	            |        |       |                  |     	    |       	  |[FP](http://saturn:9001)
				|	            |        |       |                  |     	    |       	  |[OP](http://saturn:9006)    sunlights/sunlights.1234!
				|	            |        |       |                  |     	    |       	  |nginx    80:FP测试库 9004:FP测试库 9005:FP开发库
EARTH	        |GitLab服务器	|4G	     |40G	 |192.168.0.96	    |root	    |zse4rfvgy7,./|[GitLab](http://earth)
				|	            |        |       |                  |sunlights	|zse4rfvgy7,./|	
MARS	        |Dev服务器	    |8G	     |40G	 |192.168.0.95	    |root	    |zse4rfvgy7,./|jdbc:postgresql://mars:5432/sunlightsdev   sunlights/sunlights
				|               |        |       |                  |admin	    |zse4rfvgy7	  |[FP](http://mars:9005)
				|			    |        |       |                  |           |             |[OP](http://mars:9006)sunlights/sunlights.1234!
				|			    |        |       |                  |           |             |[Jenkins](http://mars:8080)
VENNS	        |文档服务器	    |1G	     |40G	 |192.168.0.94	    |admin	    |zse4rfvgy7,./|													
SH-YIYUE-V101	|Vagrant宿主机	|		 |       |192.168.0.89	    |root	    |zse4rfvgy7,./|	
				|	            |	     |       |	                |admin      |zse4rfvgy7   |	
vagrant88		|               |        |	     |192.168.0.88	    |vagrant	|vagrant	  |ssh vagrant@192.168.0.88:2222
         		|               |        |	     |          	    |       	|       	  |jdbc:postgresql://192.168.0.88:5432/sunlightsdev   sunlights/sunlights														
阿里服务器		|               |        |	     |          	    |       	|       	  |					
ngix-http	    |ngix-http	    |4G		 |       |121.40.204.123(公) 10.168.76.12(内)|   root   |     6mOu9cIb  	  |	http://121.40.204.123:9006(op)			
				|               |        |	     |          	    |admin	    |zse4rfvgy7	  |[Nginx](http://121.40.204.123/)
finplat-1	    |finplat-1	    |4G	     |100G	 |10.168.208.241(内)	|root	    |6mOu9cIb	  |jdk(1.7.0_67)
				|               |        |	     |          	    |admin	    |zse4rfvgy7	  |http://localhost:9000(fp)
pgDB-1	        |4G	            |100G	 |       |10.168.211.45(内)	|root	    |6mOu9cIb	  |jdbc:postgresql://localhost:5432/sunlights   sunlights/sunlights
				|               |        |	     |          	    |admin	    |zse4rfvgy7	  |
pgDB-Slave	    |i-23q0fd3m2	|4G      |100G	 |10.251.236.185	|root	    |iWantaD0g	  |
PG-Master-slave |               |	     |       |                  |           |             |/venns/user/public/document/pgPool-config.txt
Master		    |	            |        |       |192.168.0.85	    |vagrant	|vagrant	  |
Slave		    |	            |        |       |192.168.0.86      |vagrant	|vagrant	  |
Archive, JIRA,[Mantis](http://192.168.0.87/mantis/)|	            |        |       |192.168.0.87		|vagrant    |vagrant	  | 	



## API service 

* 测试环境的base URL： http://192.168.0.97/api/
* 开发环境的base URL： http://192.168.0.97:9005/api/
* 生成环境的base URL： http://121.40.204.123/api/


