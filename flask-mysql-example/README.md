## Docker Compose
Install the containers.
Run the following commands from inside the frontend.git folder.

```
$ docker-compose -f docker-compose.deploy.yml up -d
```
Check that all the containers are running
```
$ docker-compose ps 

CONTAINER ID        IMAGE                  COMMAND                  CREATED             STATUS              PORTS                    NAMES
c193f5e1177b        frontendgit_order      "python app.py"          18 hours ago        Up 20 seconds       0.0.0.0:8083->5000/tcp   frontendgit_order_1
cb6a8f7f5e34        frontendgit_product    "python app.py"          18 hours ago        Up 21 seconds       0.0.0.0:8081->5000/tcp   frontendgit_product_1
195cdcf889d3        frontendgit_user       "python app.py"          18 hours ago        Up 20 seconds       0.0.0.0:8082->5000/tcp   frontendgit_user_1
8589f3eaa1d9        frontendgit_frontend   "/bin/sh -c 'python …"   18 hours ago        Up 21 seconds       0.0.0.0:80->5000/tcp     frontendgit_frontend_1
cee1a3965390        mysql:5.7.22           "docker-entrypoint.s…"   18 hours ago        Up 21 seconds       3306/tcp                 frontendgit_product_db_1
f63fb7b63efb        mysql:5.7.22           "docker-entrypoint.s…"   18 hours ago        Up 21 seconds       3306/tcp                 frontendgit_user_db_1
798bec4eb1b9        mysql:5.7.22           "docker-entrypoint.s…"   18 hours ago        Up 21 seconds       3306/tcp                 frontendgit_order_db_1
```

## To rebuild the Docker images and recreate the containers
```
$ docker-compose -f docker-compose.deploy.yml build
```
Then run the following to recreate the containers
```
$ docker-compose -f docker-compose.deploy.yml up -d
```
## Add products
```
docker exec -i frontendgit_product_1 python add_products.py
```