# scjtqs服务站的ddns 的docker环境包

## 使用方法 支持 armhf,arm64,amd64和i386，其余没有支持的，请使用dockerfile/通用 里面的Dockerfile自行docker build

### For docker-compose

> 将项目 下载下来，放入你的服务器目录 eg: /home/my/ddns

> 从wx.scjtqs.com下载专属的ddns.php文件，放入 /home/my/ddns中去

> cd /home/my/ddns 

> 确保当前文件夹下有:docker-compose.yml 和ddns.php两个文件

> docker-compose up -d 接口已启动了

### For docker 

> 从wx.scjtqs.com下载专属的ddns.php文件，放入 /home/my/ddns中去

> docker run --network=host -d -v /home/my/ddns/ddns.php:/path/ddns.php --name ddns --restart=always scjtqs/ddns:latest

### For docker build 

> 将 dockerfile/通用/Dockerfile 复制到当前目录下,然后运行下面命令 （最后那个点别忘了）

> docker build -t scjtqs/ddns:latest .

> build完成后就可以用上面两个（for docker-compose 和 for docker）方法运行了