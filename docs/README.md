# 巡检问题修复

> An awesome project.

# 配置Resin url编码
1. 修改resin.conf或resin.xml
2. 去掉 ```<character-encoding>utf-8</character-encoding>``` 注释


# 配置主机名到IP的解析
1. 使用 vi 编辑器打开 /etc/hosts 文件
   
    ```vi /etc/hosts```
2. 在文件尾部添加内容，格式：IP地址 主机名（中间用空格分隔），保存退出
   
   ``` 192.168.80.157 ecology```

# TIME-WAIT连接数过多

1. 设置nginx upstram 中keepalive 300;
   
   ``` keepalive 300; ```
2. 配置proxy_http_version 1.1; proxy_set_header Connection "Keep-Alive";
   
   ``` 
      proxy_http_version 1.1;
      proxy_set_header Connection "Keep-Alive";
   ```
3. 参考图片![nginx-keepalive.png](./assets/nginx-keepalive.png)

# Windows服务器配置交换内存

① 鼠标右击【此电脑】图标，弹出菜单选择【属性】。

![avatar](./assets/此电脑.png)

② 弹出系统窗口,点击左边子菜单【高级系统设置】。

![avatar](./assets/高级系统设置.png)

③ 系统属性窗口点击【高级】子菜单，点击性能下的【设置】。

![avatar](./assets/高级.png)

④ 在虚拟内存窗口中，首先取消自动管理所有驱动器的分页大小，点击最后一个分区F盘，选择自定义大小，初始大小和最大值都填入相同的数字，一般为物理内存x1024x2。如 物理内存8G,则设置为 8x1024x2为16384, 点击【设置】。

![avatar](./assets/更改.png)

⑤ 已经设置了F盘的虚拟内存，就可以取消C盘的虚拟内存了，选择C盘，选择无分页文件，点击【设置】。


![avatar](./assets/c无分页.png)

⑥ 提示分页文件小于800MB会发生系统错误，由于设置了F盘足够大的虚拟内存，可以忽略提示，点击【是】。

![avatar](./assets/报错.png)

⑦ 可以看到所有盘符里只有F盘有分页文件，点击【确定】。

![avatar](./assets/无分页.png)

⑧ 重新启动服务器，再次看到F盘的空间有变化了，被占用的就是分页文件，也就是虚拟内存。

![avatar](./assets/生效.png)

**本文部分图片来自https://blog.csdn.net/meigang2012/article/details/77505485**

# 禁用Resin热部署

<a href="assets/stophotdeploy.jar" target="_blank">stophotdeploy.jar</a>
## Resin4热部署补丁包操作

1、停OA服务

2、将附件stophotdeploy.jar 更新到生产Resin目录下。

3、修改Resin的配置文件resin.properties（相对路径 Resin/conf/resin.properties）

4、将resin.properties 内的jvm_args：参数内容上，加上  -javaagent:stophotdeploy.jar

例如：

   ``` jvm_args  : -javaagent:stophotdeploy.jar -Xmx5500m -Xms5500m -XX:ParallelGCThreads=20 -XX:+UseConcMarkSweepGC -XX:+UseParNewGC -XX:+DisableExplicitGC -javaagent:wagent.jar  ```
 
5、启动oa服务即可


## Resin3热部署补本包操作
1、停OA服务

2、将附件stophotdeploy.jar 更新到生产Resin目录下。

3、修改Resin的配置文件resin.conf（相对路径 Resin/conf/resin.conf）

4、在resin.conf 内的<jvm-arg>-XX:+DisableExplicitGC</jvm-arg>  下一行，加上 <jvm-arg>-javaagent:stophotdeploy.jar</jvm-arg>

例如：

      <jvm-arg>-XX:ParallelGCThreads=20</jvm-arg>
      <jvm-arg>-XX:+UseConcMarkSweepGC</jvm-arg>
      <jvm-arg>-XX:+UseParNewGC</jvm-arg>
      <jvm-arg>-XX:+DisableExplicitGC</jvm-arg>
	  <jvm-arg>-javaagent:stophotdeploy.jar</jvm-arg>
	  
5、启动oa服务即可

# EMP配置线程日志打印

1. 修改/usr/emp/appsvr/tomcat/webapps/ROOT/WEB-INF/web.xml添加以下serverlet
 ```
 <servlet> 
 <servlet-name>InitMonitor</servlet-name>
	<servlet-class>weaver.general.MonitorServer</servlet-class>
	<init-param>
		<param-name>serverName</param-name>
		<param-value>ecology</param-value>
	</init-param>
	<load-on-startup>2</load-on-startup>
</servlet>

```

2. 覆盖补丁包tomcat_EM7.zip即可

      <a href="assets/tomcat_EM7.zip" target="_blank">tomcat_EM7.zip</a>