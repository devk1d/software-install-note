
备份 sources.list

``` 
cd /etc/apt/
cp sources.list sources.list.bak

```


然后更换阿里云的源，一键脚本


```
Codename=$( (lsb_release -a)|awk '{print $2}'|tail -n 1 )
echo "\
deb http://mirrors.aliyun.com/ubuntu/ $Codename main multiverse restricted universe
deb http://mirrors.aliyun.com/ubuntu/ $Codename-backports main multiverse restricted universe
deb http://mirrors.aliyun.com/ubuntu/ $Codename-proposed main multiverse restricted universe
deb http://mirrors.aliyun.com/ubuntu/ $Codename-security main multiverse restricted universe
deb http://mirrors.aliyun.com/ubuntu/ $Codename-updates main multiverse restricted universe
deb-src http://mirrors.aliyun.com/ubuntu/ $Codename main multiverse restricted universe
deb-src http://mirrors.aliyun.com/ubuntu/ $Codename-backports main multiverse restricted universe
deb-src http://mirrors.aliyun.com/ubuntu/ $Codename-proposed main multiverse restricted universe
deb-src http://mirrors.aliyun.com/ubuntu/ $Codename-security main multiverse restricted universe
deb-src http://mirrors.aliyun.com/ubuntu/ $Codename-updates main multiverse restricted universe ">sources.list
apt-get update

```


参考：[http://www.cnblogs.com/lyon2014/p/4715379.html](http://www.cnblogs.com/lyon2014/p/4715379.html)
