## git

### 1. github 访问慢

国内访问GitHub总会遇到下载速度缓慢、链接意外终止的情况。

1. 找到本机的 `hosts` 文件

   ```
   C:\Windows\System32\drivers\etc
   ```

2. 追加域名 ip

   通过[查看域名ip](https://www.ipaddress.com/) 来获得以下两个GitHub域名的IP地址：

   (1) github.com

   (2) github.global.ssl.fastly.net

   把获取的两段`IP`写入`hosts` 文件中 

   ```
   140.82.114.4     github.com
   199.232.69.194   github.global.ssl.fastly.net
   ```

3. 刷新 `DNS` 缓存

   ```
   ipconfig /flushdns
   ```

   