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
