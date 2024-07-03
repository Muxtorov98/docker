
docker containers: **php, nginx** and **mysql** 

## Installation

Run docker containers <br>
```docker compose up -d```

Install composer scripts:<br>
```docker compose exec php composer install```

## Docker
For enter to php container run 
```docker compose exec php bash```

For enter to mysql container run 
```docker compose exec mysql bash```

For enter to nginx container run 
```docker compose exec nginx bash```

You can change containers prefix by changing ```DOCKER_PROJECT_NAME``` variable in [.env](.env) file.  

Also, you can change public ports of nginx and mysql by changing ```DOCKER_NGINX_PORT``` and ```DOCKER_DATABASE_PORT```

Database allows connections only from localhost. 
Because of this when you use the project on production and want to connect to database from your computer
you should connect via ssh bridge.
