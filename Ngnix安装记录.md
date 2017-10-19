## Ubuntu

### 使用apt-get安装nginx

> sudo apt-get install nginx


这是最简单的方法，但是这不是最新的nginx，如果需要支持http2，至少需要nginx 1.9.5，因此我们选择本地编译最新的 nginx 安装



wget https://nginx.org/download/nginx-1.10.1.tar.gz
tar -xvf nginx-1.10.1.tar.gz
cd nginx-1.10.1

# 安装编译依赖
sudo apt-get install make libssl-dev zlib zlib-devel zlib1g-dev openssl openssl-devel pcre-devel \
    libpcre3-dev libpcre++-dev

# 编译安装
./configure --with-http_ssl_module --with-http_realip_module --with-http_addition_module --with-http_sub_module \
    --with-http_dav_module --with-http_flv_module --with-http_mp4_module --with-http_gunzip_module \
    --with-http_gzip_static_module --with-http_random_index_module --with-http_secure_link_module \
    --with-http_stub_status_module --with-http_auth_request_module --with-mail --with-mail_ssl_module \
    --with-file-aio --with-ipv6 --with-cc-opt='-O2 -g -pipe -Wp,-D_FORTIFY_SOURCE=2 -fexceptions -fstack-protector --param=ssp-buffer-size=4 -m64 -mtune=generic' \
    --with-http_v2_module
make
sudo make install


# 之后nginx将安装至 /usr/local/nginx目录
# 创建一个nginx命令软连接
sudo ln -s /usr/local/nginx/sbin/nginx /usr/local/sbin/nginx
# 之后就可以运行`nginx`命令了
nginx -V

# 配置nginx的自动启动
# 下载init.d/nginx文件
sudo wget https://raw.githubusercontent.com/JasonGiedymin/nginx-init-ubuntu/master/nginx -O /etc/init.d/nginx
sudo chmod +x /etc/init.d/nginx
# 添加开机自动启动
sudo update-rc.d -f nginx defaults

# 启动
sudo /etc/init.d/nginx start  
#　sudo /etc/init.d/nginx stop  # 停止
#　sudo /etc/init.d/nginx restart  # 重启
