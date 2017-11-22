
各平台都可以通过包管理软件安装，安装教程：[https://nodejs.org/en/download/package-manager/](https://nodejs.org/en/download/package-manager/)

更好npm源： 
    npm config set registry https://registry.npm.taobao.org


Nginx 端口转发：

    server {

        listen 80 default_server;
        listen [::]:80 default_server ipv6only=on;

        server_name localhost;

        location / {
            proxy_pass http://localhost:3000;
            proxy_http_version 1.1;
            proxy_set_header Upgrade $http_upgrade;
            proxy_set_header Connection 'upgrade';
            proxy_set_header Host $host;
            proxy_cache_bypass $http_upgrade;
        }   


        location ~ /\.ht {
            deny all;
        }

    }


