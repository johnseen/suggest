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

![avatar](https://img-blog.csdn.net/20170823142933426)

② 弹出系统窗口,点击左边子菜单【高级系统设置】。

![avatar](https://img-blog.csdn.net/20170823143043894)

③ 系统属性窗口点击【高级】子菜单，点击性能下的【设置】。

![avatar](https://img-blog.csdn.net/20170823143323693)

④ 在虚拟内存窗口中，首先取消自动管理所有驱动器的分页大小，点击最后一个分区F盘，选择自定义大小，初始大小和最大值都填入相同的数字，12*1024*2。点击【设置】。

![avatar](https://img-blog.csdn.net/20170823143535038)

⑤ 已经设置了F盘的虚拟内存，就可以取消C盘的虚拟内存了，选择C盘，选择无分页文件，点击【设置】。


![avatar](https://img-blog.csdn.net/20170823143842671)

⑥ 提示分页文件小于800MB会发生系统错误，由于设置了F盘足够大的虚拟内存，可以忽略提示，点击【是】。

![avatar](https://img-blog.csdn.net/20170823144145086)

⑦ 可以看到所有盘符里只有F盘有分页文件，点击【确定】。

![avatar](https://img-blog.csdn.net/20170823144342576)

⑧ 重新启动服务器，再次看到F盘的空间有变化了，被占用的就是分页文件，也就是虚拟内存。

![avatar](https://img-blog.csdn.net/20170823144525559)

**本文部分图片来自https://blog.csdn.net/meigang2012/article/details/77505485**