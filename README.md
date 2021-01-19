# WordPress Local Development: with Nginx + Mariadb in Docker

## Before Start 

Setup proper file permissions of wp-content folder so that you can use your favorite editor

There is a default USER environment variable which hold the user name of current logged-in user. We will use these variables in our docker-compose.yml file and create two environment variables to be used inside wordpress container.

Find out your user name and id by 
```
id YOUR_USERNAME
```

and copy and paste the the value in .env-sample
```
LOCAL_USER_ID=sample_id
LOCAL_USER_NAME=sample_user
```

## Start 

 * Edit the .env-sample file with custom value, change its name to .env
 * change the server_name in nginx.conf file to your custom domain

```
docker-compose build 
docker-compose up -d
```

### Useful commands for debug

```
docker-compose build --no-cache
docker-compose up -d db
docker-compose up -d wp
docker-compose up -d nginx
docker-compose up -d php-myadmin
docker container logs CONTAINER_NAME
```

### Reference Link about file permissions in host machine and docker container

* Thanks to Rajinder Deol for scripts of setting up proper file permissions 
* [Rajinder's post](https://rajislearning.com/wordpress-development-with-docker-compose/)
* More about Permission 
    * [Avoiding Permission Issues With Docker-Created Files](https://vsupalov.com/docker-shared-permissions/)
    * [Add or Remove a User from a Group](https://www.tecmint.com/add-or-remove-user-from-group-in-linux/)
    * [Add a User to Group www-data](https://www.cyberciti.biz/faq/ubuntu-add-user-to-group-www-data/)
    * [Bind mount and permissions](https://github.com/BretFisher/ama/issues/65#issuecomment-526792333)

