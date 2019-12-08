# scjtqs服务站的ddns for ipv6的docker环境包

## 使用方法 支持 armhf,arm64,amd64和i386

### For docker-compose

> 将项目 下载下来，放入你的服务器目录 eg: /home/my/ddns

> 从wx.scjtqs.com下载专属的ddns.php文件，放入 /home/my/ddns中去

> cd /home/my/ddns 

> 确保当前文件夹下有:docker-compose.yml 和ddns.php两个文件

> docker-compose up -d 接口已启动了

### For docker 

> 从wx.scjtqs.com下载专属的ddns.php文件，放入 /home/my/ddns中去

> docker run --network=host -d -v /home/my/ddns/ddns.php:/path/ddns.php --name ddns --restart=always scjtqs/ddns:latest