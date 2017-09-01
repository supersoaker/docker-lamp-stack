# docker-lamp-stack
just a lightweight lamp stack (linux - apache - mysql - php) with docker

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

### Configuration
To enable new vhosts:
- add a new configuration file like "sites-enabled/{{your-new-vhost}}.conf"
- create the directories "sites/{{your-new-vhost}}/html" and "sites/{{your-new-vhost}}/log"
- adding the new domain to your local "/etc/hosts" file like "127.0.0.1 {{your-new-vhost}}"
Afterwards just execute:
```
docker-compose -it lamp_apache_php /etc/init.d/apache2 reload
```
To see an example just look on sites-enabled/test.localhost.conf
