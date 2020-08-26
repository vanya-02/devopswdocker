# Part 1
### Exercise 1.1
```
flipvm@flipvm-VirtualBox:~$ docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                          PORTS               NAMES
427c1202e456        nginx               "/docker-entrypoint.…"   2 minutes ago       Exited (0) About a minute ago                       compassionate_dewdney
969101b4872e        nginx               "/docker-entrypoint.…"   2 minutes ago       Exited (0) About a minute ago                       kind_sutherland
dce9b39db4ec        nginx               "/docker-entrypoint.…"   2 minutes ago       Up 2 minutes                    80/tcp              intelligent_taussig
```
### Exercise 1.2
```
flipvm@flipvm-VirtualBox:~$ docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
flipvm@flipvm-VirtualBox:~$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
```
### Exercise 1.3
Command used: `docker run -it devopsdockeruh/pull_exercise`
Secret message:
```
Give me the password: basics
You found the correct password. Secret message is:
"This is the secret message"
```
### Exercise 1.4
Commands given:
```
flipvm@flipvm-VirtualBox:~$ docker run -d devopsdockeruh/exec_bash_exercise
b9dd76fde4f6849293447a28f3ff0642a7b55ce09c6d2b57b449c9f001629e18
flipvm@flipvm-VirtualBox:~$ docker exec -it b9dd76fde4f6849293447a28f3ff0642a7b55ce09c6d2b57b449c9f001629e18 bash
root@b9dd76fde4f6:/usr/app# tail -f logs.txt 
```
Output of `tail -f logs.txt`:
```
Secret message is:
"Docker is easy"
Wed, 26 Aug 2020 02:05:30 GMT
Wed, 26 Aug 2020 02:05:33 GMT
Wed, 26 Aug 2020 02:05:36 GMT
Wed, 26 Aug 2020 02:05:39 GMT
Secret message is:
"Docker is easy"
Wed, 26 Aug 2020 02:05:45 GMT
```
### Exercise 1.5
Command used to start the process (includes fix for missing curl):
```
flipvm@flipvm-VirtualBox:~$ docker run -it ubuntu:16.04 sh -c 'apt-get update && apt-get install -y curl;\
> echo "Input website:";\
> read website;\
> echo "Searching..";\
> sleep 1;\
> curl http://$website;'
```
### Exercise 1.6
[Dockerfile](1.6/Dockerfile):
```
FROM devopsdockeruh/overwrite_cmd_exercise
CMD ["-c"]
```
Command used to build the image: `docker build -t docker-clock .`

Command to run the container: `docker run docker-clock`
### Exercise 1.7
[Dockerfile](1.7/Dockerfile):
```
FROM devopsdockeruh/overwrite_cmd_exercise
CMD ["-c"]
```
Command used to build the image: `docker build -t curler .`
Command used to run the container: `docker run --rm -it curler`
### Exercise 1.8
Commands used:
```
$ touch host_logs.txt
$ docker run --rm -itv $(pwd)/host_logs.txt:/usr/app/logs.txt devopsdockeruh/first_volume_exercise
Wrote to file /usr/app/logs.txt
Wrote to file /usr/app/logs.txt
^C
```
Check logs created in our filesystem:
```
$ cat host_logs.txt
Wed, 26 Aug 2020 04:22:59 GMT
Wed, 26 Aug 2020 04:23:02 GMT
```
### Exercise 1.9
```
docker run -dp 80:80 devopsdockeruh/ports_exercise
```
### Exercise 1.10
[Dockerfile](1.10/Dockerfile):
```
FROM ubuntu:16.04
WORKDIR /mydir
COPY frontend-example-docker/ .
RUN apt-get update && apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash
RUN apt-get install -y nodejs && npm install
EXPOSE 5000
CMD npm start
```
Build and run:
`docker build -t fr-end .`
`docker run --rm -dp 5000:5000 fr-end`
### Exercise 1.11
[Dockerfile](1.11/Dockerfile):
```
FROM ubuntu:16.04
WORKDIR /mydir
COPY backend-example-docker/ .
RUN apt-get update && apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash
RUN apt-get install -y nodejs && npm install
EXPOSE 8000
CMD npm start
```
Messages written from container to (host_logs.txt)[1.11/host_logs.txt]:
```
8/26/2020, 5:37:37 AM: Connection received in root
8/26/2020, 5:37:39 AM: Connection received in root
8/26/2020, 5:38:46 AM: Connection received in root
8/26/2020, 5:38:47 AM: Connection received in root
8/26/2020, 5:38:47 AM: Connection received in root
```
Commands used:
```
$ touch logs.txt
$ docker build -t b-end .
$ docker run -d -p 8000:8000 -v $(pwd)/host_logs.txt:/mydir/logs.txt b-end
```
### Exercise 1.12




