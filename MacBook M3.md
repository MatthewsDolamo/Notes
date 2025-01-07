# MacBook M3

## Nginx
``` 
cd /opt/homebrew/etc/nginx/servers/
cd /opt/homebrew/etc/nginx/nginx.conf


brew services start nginx
brew services restart nginx
``` 
## MySQL
brew services start mysql

## PHP 8.2
```
brew services start php@8.3
brew services start php@8.2
brew services start php@7.4

sudo vi /opt/homebrew/etc/php/8.2/php-fpm.d/www.conf

echo 'export PATH="/opt/homebrew/opt/php@8.2/bin:$PATH"' >> ~/.zshrc
echo 'export PATH="/opt/homebrew/opt/php@8.2/sbin:$PATH"' >> ~/.zshrc

PHP 7.4
brew services restart shivammathur/php/php@7.4

echo 'export PATH="/opt/homebrew/opt/php@7.4/bin:$PATH"' >> ~/.zshrc
echo 'export PATH="/opt/homebrew/opt/php@7.4/sbin:$PATH"' >> ~/.zshrc
``` 
## Redis
```
Pecl install ev
Peel install redis
``` 

brew install node@21

Update and upgrade and check if everything still fine
brew update && brew upgrade && brew autoremove && brew doctor

to start the Reverb socket server, you run 
php artisan reverb:start 

## Restart
brew unlink php && brew link --overwrite --force shivammathur/php/php@8.3 && brew services restart php

source ~/.zshrc

cat ~/.ssh/id_ed25519.pub | pbcopy

## View installed
sudo apt list --installed | grep ‘php’
