# XAMPP Home Directory Setup (Apache DocumentRoot → `~/Projects/php`)

Move XAMPP’s web root from `/opt/lampp/htdocs` to a directory in your **home** so you can work under your user account with clean permissions.

## 1) Prepare your project path

```bash
# 1) make sure the path exists
mkdir -p /home/ihtisham/Projects/php

# 2) put a test file
echo "<?php echo 'OK from '.__FILE__; phpinfo(); ?>" > /home/ihtisham/Projects/php/index.php

# 3) ownership (you own your project)
sudo chown -R ihtisham:ihtisham /home/ihtisham/Projects/php

# 4) directory perms (execute bit needed to traverse)
chmod 711 /home/ihtisham
chmod 755 /home/ihtisham/Projects
chmod 755 /home/ihtisham/Projects/php

# 5) file perms (typical web-safe)
find /home/ihtisham/Projects/php -type d -exec chmod 755 {{}} \;
find /home/ihtisham/Projects/php -type f -exec chmod 644 {{}} \;
```

> If you don’t want to open your home dir with `711`, use an ACL on `/home/ihtisham` to grant Apache read/execute instead.

## 2) Point Apache to this exact path

Open the main Apache config in XAMPP (needs sudo because `/opt`):

```bash
sudo nano /opt/lampp/etc/httpd.conf
```

Change both **DocumentRoot** and the matching **Directory** block to your path:

```apache
DocumentRoot "/home/ihtisham/Projects/php"

<Directory "/home/ihtisham/Projects/php">
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
    DirectoryIndex index.php index.html
</Directory>
```

Save & exit, then restart XAMPP:

```bash
sudo /opt/lampp/lampp restart
```

### Nano tip

Use **Ctrl+W**, type `DocumentRoot`, and press **Enter** to jump to the section quickly.