Finally, check DirectoryIndex includes index.php
    DirectoryIndex index.php index.html

The php.ini and php-fpm.ini file can be found in:
    /opt/homebrew/etc/php/8.3/

php@8.3 is keg-only, which means it was not symlinked into /opt/homebrew,
because this is an alternate version of another formula.

If you need to have php@8.3 first in your PATH, run:
  echo 'export PATH="/opt/homebrew/opt/php@8.3/bin:$PATH"' >> ~/.zshrc
  echo 'export PATH="/opt/homebrew/opt/php@8.3/sbin:$PATH"' >> ~/.zshrc

For compilers to find php@8.3 you may need to set:
  export LDFLAGS="-L/opt/homebrew/opt/php@8.3/lib"
  export CPPFLAGS="-I/opt/homebrew/opt/php@8.3/include"

To start shivammathur/php/php@8.3 now and restart at login:
  brew services start shivammathur/php/php@8.3
Or, if you don't want/need a background service you can just run:
  /opt/homebrew/opt/php@8.3/sbin/php-fpm --nodaemonize
