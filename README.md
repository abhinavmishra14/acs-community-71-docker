# README #

### Server properties
#### Make sure to add entries in host file (c:\Windows\System32\Drivers\etc\hosts). e.g.:
#### 127.0.0.1 alfresco.local.com
#### localhost alfresco.local.com

### To create the external volumes use following command:

`docker volume create <volumeName>`

### To purge the external volumes use following command:

`docker volume rm -f <volumeName>`

### To build use following command:

- To build the images, This command will ignore any images which are already built and no changes to DockerFile has been identified. It will use cache.

`docker-compose -f ./docker-compose.yml build`

- To build the images with no cache. It will force rebuild

`docker-compose -f ./docker-compose.yml build --no-cache`


### To launch containers use following command:

`docker-compose -f ./docker-compose.yml up`


### To build and launch containers use following command:

`docker-compose -f ./docker-compose.yml up --build`


### To shutdown use following command:

`docker-compose -f ./docker-compose.yml down`

### To tail logs use following command:

`docker-compose -f ./docker-compose.yml logs -f`