# Part 2
### Exercise 2.1
[Docker-compose](2.1/docker-compose.yml):
```
version: '3'

services:
  first_volume_exercise:
    image: devopsdockeruh/first_volume_exercise
    volumes:
      - ./host_logs.txt:/usr/app/logs.txt
    container_name: ex_2.1
```
Output of [host_logs.txt](2.1/host_logs.txt):
```
Mon, 31 Aug 2020 01:53:48 GMT
Mon, 31 Aug 2020 01:53:51 GMT
Mon, 31 Aug 2020 01:53:54 GMT
Mon, 31 Aug 2020 01:53:57 GMT
Secret message is:
"Volume bind mount is easy"
Mon, 31 Aug 2020 01:54:03 GMT
```
### Exercise 2.2
[Docker-compose](2.2/docker-compose.yml):
```
version: '3.5'

services:
  ports_exercise:
    image: devopsdockeruh/ports_exercise
    container_name: "2.2"
    ports:
      - 80:80
```
### Exercise 2.3
[docker-compose.yml](2.3/docker-compose.yml):
```
version: '3.5'

services:
  front_end:
    build:
      context: .
      dockerfile: Dockerfile-frontend
    ports:
      - "5000:5000"
    container_name: "front_end"

  back_end:
    build:
      context: .
      dockerfile: Dockerfile-backend
    ports:
      - "8000:8000"
    volumes:
      - ./host_logs.txt:/mydir/logs.txt
    container_name: "back_end"
```
Reused dockerfiles from 1.12 (there's also the possibility of re-using the images built in 1.12 but I went with the former):

[Dockerfile-frontend](../part1/1.12/Dockerfile-frontend):
```
FROM ubuntu:16.04
WORKDIR /mydir
COPY frontend-example-docker/ .
RUN apt-get update && apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash
RUN apt-get install -y nodejs && npm install
EXPOSE 5000
ENV API_URL=http://localhost:8000
CMD npm start
```
[Dockerfile-backend](../part1/1.12/Dockerfile-backend):
```
FROM ubuntu:16.04
WORKDIR /mydir
COPY backend-example-docker/ .
RUN apt-get update && apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash
RUN apt-get install -y nodejs && npm install
EXPOSE 8000
ENV FRONT_URL=http://localhost:5000
CMD npm start
```
### Exercise 2.4
Command used: `docker-compose up --scale compute=3`

### Exercise 2.5
[docker-compose.yml](2.5/docker-compose.yml):
```
version: '3.5'

services:
  front_end:
    image: fr-end
    ports:
      - 5000:5000
    container_name: "front_end"

  back_end:
    image: b-end
    ports:
      - 8000:8000
    volumes:
      - ./host_logs.txt:/mydir/logs.txt
    container_name: "back_end"
    environment:
      - REDIS=redis
      - REDIS_PORT=6379

  redis:
    image: redis
    ports:
      - 6379:6379
```

### Exercise 2.6
