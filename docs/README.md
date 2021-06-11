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
   ``` proxy_http_version 1.1;
       proxy_set_header Connection "Keep-Alive";
   ```
3. 参考图片![nginx-keepalive.png](./assets/nginx-keepalive.png)