# Installing prodcution-ready Magento on Ubuntu

## 1. Overall
- Ubuntu 22.04 LTS
- Magento 2.4.7

## 2. Magento Depencdency 
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install curl wget gnupg unzip -y

```
### 2. PHP: 8.2
```bash
sudo add-apt-repository ppa:ondrej/php
sudo apt update
sudo apt install php8.2 php8.2-fpm php8.2-cli php8.2-mysql php8.2-curl php8.2-mbstring php8.2-intl php8.2-xml php8.2-zip php8.2-bcmath php8.2-soap php8.2-gd -y
php -v
sudo systemctl enable php8.2-fpm
sudo systemctl start php8.2-fpm
```
### 3. Database: MariaDB 10.6
```bash
sudo apt install software-properties-common -y
sudo add-apt-repository 'deb [arch=amd64,arm64,ppc64el] http://mirror.kumi.systems/mariadb/repo/10.6/ubuntu focal main'
sudo apt update
sudo apt install mariadb-server -y
sudo mysql_secure_installation
sudo mysql -u root -p
```

```mysql
CREATE DATABASE magento;
CREATE USER 'magento_user'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON magento.* TO 'magento_user'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```
### 4. Elasticsearch: Required for Magento 2.4.7
```bash
curl -fsSL https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo gpg --dearmor -o /usr/share/keyrings/elasticsearch-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/8.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-8.x.list
sudo apt update
sudo apt install elasticsearch -y
sudo systemctl enable elasticsearch
sudo systemctl start elasticsearch
```
### 5. Composer: Required for dependency management
```bash
curl -sS https://getcomposer.org/installer | php
sudo mv composer.phar /usr/local/bin/composer
composer --version
```
### 6. Web Server: Nginx
```bash
sudo apt install nginx -y
sudo vi /etc/nginx/sites-available/magento
```

```yaml
server {
    listen 80;
    server_name your-domain.com;
    set $MAGE_ROOT /var/www/html/magento;
    set $MAGE_MODE production;

    root $MAGE_ROOT/pub;

    index index.php;

    location / {
        try_files $uri $uri/ /index.php$is_args$args;
    }

    location ~ \.php$ {
        try_files $uri =404;
        fastcgi_pass unix:/var/run/php/php8.2-fpm.sock;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include fastcgi_params;
    }

    location ~* \.(js|css|png|jpg|jpeg|gif|ico|svg|eot|ttf|woff|woff2)$ {
        expires max;
        log_not_found off;
    }

    error_page 404 /errors/404.php;
    location /errors/ {
        internal;
    }
}
```

```bash
sudo ln -s /etc/nginx/sites-available/magento /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl restart nginx
```
- Tạo 1 symbolic link

## 7. Magento installation
- Use composer to download magento
```bash
cd /var/www/html
composer create-project --repository=https://repo.magento.com/ magento/project-community-edition magento
sudo chown -R www-data:www-data /var/www/html/magento
sudo find /var/www/html/magento -type d -exec chmod 770 {} \;
sudo find /var/www/html/magento -type f -exec chmod 660 {} \;
```
