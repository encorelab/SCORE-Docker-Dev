# SCORE-Docker-Dev

## Description
SCORE development uses [Docker](https://www.docker.com/). Using Docker simplifies and standardizes the development environment so that developers can quickly and easily start developing SCORE.

## Setup
1. Install Docker from [here](https://www.docker.com/products/docker-desktop).
2. In the same folder, checkout [SCORE-Docker-Dev (this project)](https://github.com/encorelab/SCORE-Docker-Dev), [SCORE-API](https://github.com/encorelab/SCORE-API), and [SCORE-Client](https://github.com/encorelab/SCORE-Client).
```
$ git clone https://github.com/encorelab/SCORE-Docker-Dev
$ git clone https://github.com/encorelab/SCORE-API
$ git clone https://github.com/encorelab/SCORE-Client
$ ls
SCORE-Docker-Dev
SCORE-API
SCORE-Client
```
3. Run ```docker compose up``` in the SCORE-Docker-Dev directory
```
$ cd SCORE-Docker-Dev
SCORE-Docker-Dev $ docker compose up
```
4. Wait for everything to download, compile, and start. This can take a while depending on your computer and connection speeds.
5. When everything is done, SCORE will be running at http://localhost:81. Go there with your browser to load the SCORE homepage.
6. Log in with admin/pass, or previewuser/wise.

Any changes that you make to the source code will be automatically compiled and reloaded in the browser. 

## Main Docker commands
1. Start/Stop development containers
```
docker-compose [up/down]
```
2. List running containers
```
docker container ls
```
3. Restart container (ex: 'score-client')
```
docker restart score-client
```
4. Access container's command line (ex: 'score-client')
```
docker exec -it score-client sh
```
5. Run 'npm test' in score-client container
```
docker exec -it score-client npm test
```
6. Run 'npm test' in score-client container with the watch option
```
docker exec -it score-client npm test -- "--watch=true"
```
7. Run 'maven test' in score-api container
```
docker exec -it score-api mvn test
```

## MySQL Docker commands
1. Connect to MySQL container (password: iamroot)
```
docker run -it --network score-docker-dev_default --rm mysql:8 mysql -hscore-mysql -uroot -p 
```
2. Import data from mysqldump
```
docker exec -i score-mysql sh -c 'exec mysql wise_database -uroot -p"$MYSQL_ROOT_PASSWORD"' < ~/path_to/wise_database_dump.sql
```
3. Dump data from MySQL container
```
docker exec -i score-mysql sh -c 'exec mysqldump wise_database -uroot -p"$MYSQL_ROOT_PASSWORD"' > wise_database_dump.sql
```

# Resources

Open-source license: GNU General Public License, v3.  See LICENSE.txt for details.
