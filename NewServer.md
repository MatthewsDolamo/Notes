<p align="center"><a href="https://decuple.co.za/" target="_blank"><img src="" width="400"></a></p>

# Quick New Server SetUp


## Customise your terminal
- https://github.com/zthxxx/jovial

## Install
- apt install --yes php7.4 php7.4-{bcmath,cli,common,curl,dom,fpm,gd,igbinary,imagick,intl,json,mbstring,mysql,opcache,readline,redis,soap,xml,zip} openssl curl wget zip unzip git mysql-server build-essential zsh nginx python3-certbot-nginx supervisor redis nodejs htop


##  Add user
- adduser user
- usermod -aG sudo user
- visudo
  
## Run Nginx as different user
- vi /etc/nginx/nginx.conf
- user userCreated
- egrep '^(user|group)' /etc/nginx/nginx.conf

## Add SSH key for root or decouple user
- mkdir -p /home/root/.ssh && touch /home/root/.ssh/authorized_keys
- chmod 700 /home/root/.ssh && chmod 600 /home/root/.ssh/authorized_keys
- chown -R root:root /home/root/.ssh
- cat ~/.ssh/id_rsa.pub | pbcopy and paste inside the Authorised_keys

## Github deployment key
- Login as decouple user and generate ssh key
- Cd ~/..ssh && ssh-keygen
- Add it to GitHub, profile -> settings -> ssh and gpg

## Run PHP as different user
- Vi /etc/php/7.4/fpm/pool.d/www.conf

``` 
user = larval
group = larval
Listen= 127.0.0.1:9000
```

## Install composer
- curl -sS https://getcomposer.org/installer -o composer-setup.php
- php composer-setup.php --install-dir=/usr/local/bin --filename=composer

## Install Node v14
- curl -sL https://deb.nodesource.com/setup_18.x -o nodesource_setup.sh && bash nodesource_setup.sh
- apt install -y nodejs
- npm install -g npm@latest

##  Add repos + update packages
- add-apt-repository ppa:ondrej/php
- add-apt-repository ppa:redislabs/redis
- curl https://nginx.org/keys/nginx_signing.key | gpg --dearmor | sudo tee /usr/share/keyrings/nginx-archive-keyring.gpg >/dev/null
- echo "deb [signed-by=/usr/share/keyrings/nginx-archive-keyring.gpg] http://nginx.org/packages/ubuntu `lsb_release -cs` nginx" | sudo tee /etc/apt/sources.list.d/nginx.list
- echo -e "Package: *\nPin: origin nginx.org\nPin: release o=nginx\nPin-Priority: 900\n" | sudo tee /etc/apt/preferences.d/99nginx
- apt update
- apt install -y software-properties-common nginx
- apt dist-upgrade -y
- apt autoremove -y


## Set server timezone (optional)
- timedatectl set-timezone Africa/Johannesburg


## Select vi as default editor
- select-editor


##  Allow members of group sudo to execute these commands
```
%sudo   ALL=(ALL:ALL) ALL
userCreated ALL=(ALL:ALL) NOPASSWD:/usr/sbin/service php7.4-fpm reload
userCreated ALL=(ALL:ALL) NOPASSWD:/usr/sbin/service php7.4-fpm restart
userCreated ALL=(ALL:ALL) NOPASSWD:/usr/sbin/service nginx reload
userCreated ALL=(ALL:ALL) NOPASSWD:/usr/sbin/service nginx restart
userCreated ALL=(ALL:ALL) NOPASSWD:/usr/sbin/service supervisor reload
userCreated ALL=(ALL:ALL) NOPASSWD:/usr/sbin/service supervisor restart
```

