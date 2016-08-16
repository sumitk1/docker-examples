To create php dev env with mysql and redis
```
check if docker is running - $ docker ps
$ docker pull mysql
$ docker pull sumitk1/lemp
$ docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=123456 -d mysql:latest
$ docker run --name some-redis -d redis
$ docker run -d -P --name fboot1 --link some-mysql:mysql --link some-redis:redis -v /Users/sumitk/projects/someProj:/srv/http sumitk1/lemp:1.0
$ 
$ docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                                            NAMES
98b200aa8197        sumitk1/lemp:1.0    "/bin/sh -c 'sh /star"   25 seconds ago      Up 24 seconds       0.0.0.0:32771->80/tcp, 0.0.0.0:32770->9000/tcp   fboot1
5b3f19164066        redis               "docker-entrypoint.sh"   2 minutes ago       Up 2 minutes        6379/tcp                                         some-redis
7609d22dabd2        mysql:latest        "docker-entrypoint.sh"   5 minutes ago       Up 5 minutes        3306/tcp                                         some-mysql
```

Go to http://localhost:32771 to see someProj application 
