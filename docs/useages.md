### windows版本

`不支持windows 2008,只支持2012以上操作系统`

1. 将巡检工具放置在ecology同级目录下

![Pasted_image_20220105120944.png](https://home.sunzhe.cc:88/2022/04/18/3eb3aee2cce27.png)

2. 解压巡检工具，并修改配置文件

![Pasted_image_20220105120949.png](https://home.sunzhe.cc:88/2022/04/18/09fab1f809534.png)

3.  配置文件说明如下

![Pasted_image_20220105120956.png](https://home.sunzhe.cc:88/2022/04/18/3923fdf2d2e43.png)

4.  配置完成开始运行start.bat如下：

![Pasted_image_20220105121007.png](https://home.sunzhe.cc:88/2022/04/18/3e0e7207816a9.png)

![Pasted_image_20220105121020.png](https://home.sunzhe.cc:88/2022/04/18/ac6dbf4ca2bc2.png)

5. 运行完成后，会在本地weaver路径生成一个”客户名”_Windows2021-08-05-13-31_192.168.81.75_WEAVERZHE.json,请将本文件，附到巡检流程里面

![Pasted_image_20220105121027.png](https://home.sunzhe.cc:88/2022/04/18/992bc1569f6cb.png)

6. SQLserver巡检说明`注意一定要放置到SQLServer主机上,不能放置到OA主机上`

![Pasted_image_20220105121035.png](https://home.sunzhe.cc:88/2022/04/18/39bf52f0b70e1.png)


`因服务器负载和配置有差异，bat窗口的运行时间可能会长会短，请耐心等待，最长不超过5分钟，如果无响应请按回车键,oa巡检,请将巡检脚本放置到oa主机上,sqlserver巡检请将巡检脚本放置到sqlserver主机上`
  ### Linux版本

   `注意所有服务器都必须上传巡检脚本,然后根据主机角色选择对应的菜单,比如oracle主机,先上传巡检脚本,然后执行menu.sh,选择oracle巡检`
  #### OA巡检

  1. 上传巡检脚本到服务器,任意位置(建议/tmp),创建巡检目录并解压
  
  `mkdir inspect && tar -zxvf Linux-inspect.tar.gz -C inspect && cd inspect`

  2. 使用shell运行脚本 `sh menu.sh`,选择需要巡检的项目,暂时支持单主机巡检,OA巡检,EMP巡检(`EM7 不支持老EM,比如EM6,Ebridge,emessage等`),Redis巡检,Nginx巡检,Oracle巡检,MySQL巡检,单OA巡检(`适用于非Resin中间件,比如tomcat,东方通等`)
  
  ![memu.png](https://home.sunzhe.cc:88/2022/04/18/4889fd421ba9d.png)

  3. 选择`2`,执行OA巡检,如下:
   
   ![oainspect.png](https://home.sunzhe.cc:88/2022/04/18/9f436efb20242.png)

  `输入oa,resin,jdk路径,如果与default一致,回车即可`

  ![oashow.png](https://home.sunzhe.cc:88/2022/04/18/70183672755f2.png)

  4. 将文件附在巡检流程里面,文件名应为`客户名_Inspection-内网IP-时间.txt`,比如`中国交通信息科技集团有限公司_Inspection-10.100.3.2-202110121449.txt`
  
  ![oaresult.png](https://home.sunzhe.cc:88/2022/04/18/dade511602410.png)

  #### EMP巡检

  `注意,EMP会自动巡检EMP所用Redis,MySQL,请勿重复执行巡检脚本,巡检redis,mysql`

  1. 上传巡检脚本到EMP服务器,任意位置(建议/tmp),创建巡检目录并解压
   
   `mkdir inspect && tar -zxvf Linux-inspect.tar.gz -C inspect && cd inspect`

  2. 执行`sh menu.sh`,选择`3`,执行EMP巡检,输入安装路径,默认为`/usr/emp`
  
  ![emptest.png](https://home.sunzhe.cc:88/2022/04/18/2903ab925324c.png)

  #### Redis巡检

  1. 上传巡检脚本到Redis服务器,任意位置(建议/tmp),创建巡检目录并解压
   
   `mkdir inspect && tar -zxvf Linux-inspect.tar.gz -C inspect && cd inspect`

  2. 执行`sh menu.sh`,选择`4`,执行Redis巡检,输入Redis端口,密码
  
  ![redisinspect.png](https://home.sunzhe.cc:88/2022/04/18/278a061fe1083.png)

  #### Nginx巡检

   1. 上传巡检脚本到Nginx服务器,任意位置(建议/tmp),创建巡检目录并解压
   
   `mkdir inspect && tar -zxvf Linux-inspect.tar.gz -C inspect && cd inspect`

  2. 执行`sh menu.sh`,选择`5`,执行Nginx巡检,输入`Nginx可执行文件路径`
  
  ![nginxinspect.png](https://home.sunzhe.cc:88/2022/04/18/9d6677723d12c.png)

  ####  Oracle巡检

  1. 上传巡检脚本到Oracle服务器,任意位置(建议/tmp),创建巡检目录并解压
   
   `mkdir inspect && tar -zxvf Linux-inspect.tar.gz -C inspect && cd inspect`

  2. 执行`sh menu.sh`,选择`6`,执行Oracle巡检,输入`OA使用的用户名`
  
  ![oracleinspect.png](https://home.sunzhe.cc:88/2022/04/18/7f827ec5b12b1.png)

  ####  MySQL巡检

  1. 上传巡检脚本到MySQL服务器,任意位置(建议/tmp),创建巡检目录并解压
   
   `mkdir inspect && tar -zxvf Linux-inspect.tar.gz -C inspect && cd inspect`

  2. 执行`sh menu.sh`,选择`7`,执行MySQL巡检,输入`参数(账号,密码,主机,端口)`
  
  ![mysqlinspect.png](https://home.sunzhe.cc:88/2022/04/18/f478edd910a11.png)

  #### Simple-Ecology巡检(适用于非resin中间件)

  1. 上传巡检脚本到OA服务器,任意位置(建议/tmp),创建巡检目录并解压
   
   `mkdir inspect && tar -zxvf Linux-inspect.tar.gz -C inspect && cd inspect`

  2. 执行`sh menu.sh`,选择`8`,执行OA巡检,输入`参数(ecology路径,jdk路径,oa端口)`
  
  ![simple-oa.png](https://home.sunzhe.cc:88/2022/04/18/80cdd55fc5c87.png)
