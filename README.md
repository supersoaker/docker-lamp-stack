# docker-lamp-stack
just a lightweight lamp stack (linux - apache - mysql5.7 - php7.1) with docker

### Usage
Make sure that: 
- docker and docker-compose are installed
- you cloned this repository into your favorite directory
- no service is currently working on port 80 or 443

Then just start the docker containers using
```
docker-compose up
```
Now you can connect to your webserver on http://localhost/ or https://localhost/ (with a non trusted certificate)

To stop the current container use
```
docker-compose down
```

### Configuration
##### New vhosts
To enable new vhosts:
- add a new configuration file like "sites-enabled/{{your-new-vhost}}.conf"
- create the directories "sites/{{your-new-vhost}}/html" and "sites/{{your-new-vhost}}/log"
- adding the new domain to your local "/etc/hosts" file like "127.0.0.1 {{your-new-vhost}}"
Afterwards just execute:
```
docker-compose -it lamp_apache_php /etc/init.d/apache2 reload
```
To see an example just look on sites-enabled/test.localhost.conf
##### Other php version
To use another php version:
- use "docker-compose down" to stop the containers
- change the first line in "php/Dockerfile" from "FROM php:7.1-apache" to "FROM php:5.6-apache" or another php version (available versions: https://github.com/docker-library/php)
- use "docker-compose build" to build the new containers
- afterwards use "docker-compose up" to start your lamp stack with the new php version

