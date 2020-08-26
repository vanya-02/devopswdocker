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

