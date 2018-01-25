# simple-lamp
Apache + PHP + MySQL .


## setup
#### Host PC
/etc/hosts (add)
```
127.0.0.1       www.dev-simple-lamp.local
127.0.0.1       admin.dev-simple-lamp.local
```

## how to use
1. cd simple-lamp/
1. docker-compose build 
1. docker-compose up

## mount volumes
| container | host_path | container_path |
----|----|----| 
| app | ./application | /usr/src/application |
| db | ./container/db/data | /var/lib/mysql |


## url
| container | url | note |
----|----|----| 
| app | http://www.dev-simple-lamp.local | allow https. (self ssl) |
| app | http://admin.dev-simple-lamp.local | allow https. (self ssl) |
| adminer | http://localhost:8080 | like phpmyadmin. [adminer](https://hub.docker.com/r/library/adminer) |
| maildev | http://localhost:1080 | [MailDev](https://github.com/djfarrelly/MailDev) |
