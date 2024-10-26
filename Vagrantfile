# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "ubuntu/focal64"

  # Create a private network for the VM with a specific IP address.
  config.vm.network "private_network", ip: "192.168.56.10"

  # Create a public network, which generally matches to bridged network.
  config.vm.network "public_network"

  # Provider-specific configuration for VirtualBox.
  config.vm.provider "virtualbox" do |vb|
      vb.memory = 1600   # Allocate 1.6 GB of RAM
      vb.cpus = 1        # Allocate 1 CPU
  end

  # Enable provisioning with a shell script.
  config.vm.provision "shell", inline: <<-SHELL
    # Update the package list to ensure the latest version of packages is installed.
    sudo apt-get update
    
    # Install required packages for the web server and MySQL.
    sudo apt-get install -y apache2 \
                    ghostscript \
                    libapache2-mod-php \
                    mysql-server \
                    php \
                    php-bcmath \
                    php-curl \
                    php-imagick \
                    php-intl \
                    php-json \
                    php-mbstring \
                    php-mysql \
                    php-xml \
                    php-zip

    # Create a directory for the WordPress installation.
    sudo mkdir -p /srv/www
    sudo chown www-data: /srv/www  # Change ownership to the web server user.

    # Download and extract the latest version of WordPress.
    curl https://wordpress.org/latest.tar.gz | sudo -u www-data tar zx -C /srv/www

    # Create a new Apache configuration file for WordPress.
    cat > /etc/apache2/sites-available/wordpress.conf <<EOF
<VirtualHost *:80>
        DocumentRoot /srv/www/wordpress
        <Directory /srv/www/wordpress>
            Options FollowSymLinks
            AllowOverride Limit Options FileInfo
            DirectoryIndex index.php
            Require all granted
        </Directory>
        <Directory /srv/www/wordpress/wp-content>
            Options FollowSymLinks
            Require all granted
        </Directory>
</VirtualHost>
EOF

    # Enable the new WordPress site and the rewrite module.
    sudo a2ensite wordpress
    sudo a2enmod rewrite

    # Disable the default site configuration.
    sudo a2dissite 000-default

    # Create the WordPress database and user with the necessary privileges.
    mysql -u root -e 'CREATE DATABASE wordpress;'
    mysql -u root -e 'CREATE USER wordpress@localhost IDENTIFIED BY "admin123";'
    mysql -u root -e 'GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP,ALTER ON wordpress.* TO wordpress@localhost;'
    mysql -u root -e 'FLUSH PRIVILEGES;'

    # Configure WordPress by copying and modifying the sample config file.
    sudo -u www-data cp /srv/www/wordpress/wp-config-sample.php /srv/www/wordpress/wp-config.php
    sudo -u www-data sed -i 's/database_name_here/wordpress/' /srv/www/wordpress/wp-config.php
    sudo -u www-data sed -i 's/username_here/wordpress/' /srv/www/wordpress/wp-config.php
    sudo -u www-data sed -i 's/password_here/admin123/' /srv/www/wordpress/wp-config.php

    # Restart MySQL and Apache services to apply changes.
    systemctl restart mysql
    systemctl restart apache2

  SHELL
end

