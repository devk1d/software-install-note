
安装：
```
  #get composer:
  curl -s https://getcomposer.org/installer | php
  # move composer into a bin directory you control:
  sudo mv composer.phar /usr/local/bin/composer

  # double check composer works
  composer about

  # (optional) Update composer:
  sudo composer self-update
```  
  
源加速：
 
方法一： 修改 composer 的全局配置文件（推荐方式）:
```
  composer config -g repo.packagist composer https://packagist.phpcomposer.com
```
方法二： 修改当前项目的 composer.json 配置文件：
```
  composer config repo.packagist composer https://packagist.phpcomposer.com
```
还在手动添加到 composer.json 文件:
```
  "repositories": {
      "packagist": {
          "type": "composer",
          "url": "https://packagist.phpcomposer.com"
      }
  }
```
