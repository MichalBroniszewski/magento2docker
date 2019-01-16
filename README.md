# Basic docker stack for Magento 2 development

### In order to install Magento 2 follow this step:

1. Obtain your magento keys: 

    https://devdocs.magento.com/guides/v2.3/install-gde/prereq/connect-auth.html
2. Create new project using Composer: 

    `composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>`
3. Move content of this repo to `<install-directory-name>`
4. Create `.env` file based on `.env.dist`
5. Add `/docker/data` directory to `.gitignore`
6. Add new host (`/etc/hosts -> 127.0.0.1 m2.loc`)

7. Set proper file permissions:

    `cd /var/www/html/<magento install directory>`
  
    `find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +`
    
    `find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +`
    
    `chown -R :www-data . # Ubuntu`
    
    `chmod u+x bin/magento`
    
    More info can be found here: 
    
    https://devdocs.magento.com/guides/v2.3/install-gde/composer.html
    
8. Run command:

    `docker-compose up -d`
9. Check whether all 3 containers are ready to go using `docker ps` command.
10. Head to `http://m2.loc` and go through the installation process. When asked for database data fill in:
- `mysql` as a mysql server (mysql container name defined in docker-compose.yml)
- `user` as a db user
- `pass` as a password
- `databse` as a database name

User, password and database name can be configured in `.env` file.

11. Enjoy!
