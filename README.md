# dmd2b-dock
Create a dock around the dmd2b project. The big advantage about dock is that you can run it from whatever machine you want but she has to get "Docker"

## Overview
This project consists on creating a dock for the dmd2b project based on the docker technology.

# Get started :

Create an image from Ubuntu dock.
```
sudo service docker start
```

Then, pull the latest ubuntu image:
```
sudo docker pull ubuntu
```

which will result in something like:
```
sudo docker pull ubuntu

Using default tag: latest
latest: Pulling from library/ubuntu
2f0243478e1f: Pull complete
d8909ae88469: Pull complete
820f09abed29: Pull complete
01193a8f3d88: Pull complete
Digest: sha256:8e2324f2288c26e1393b63e680ee7844202391414dbd48497e9a4fd997cd3cbf
Status: Downloaded newer image for ubuntu:latest
```

you can check if the image was well pulled
```
sudo docker images

REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
ubuntu              latest              0f192147631d        7 weeks ago         132.8 MB
```

Then, run the ubuntu latest image in order to get the ID container :
```
sudo docker run -it ubuntu
sudo docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                    PORTS   NAMES    
9093de564bf9        ubuntu              "/bin/bash"         7 seconds ago       Exited (0) 2 seconds ago           tiny_boyd

sudo docker commit <ID_container of Ubuntu> new_internship
```
# Bring folders from an outside system inside the dock

The problem with the container is, it is an isolated system so you have to install everything you need and basically the folders you have created with your account.

Before you lauch the dock check your uid (20064) and your username (yves)
```
id
uid=20064(yves) gid=1102(grantlab_local) groups=1102(grantlab_local),27(sudo),999(docker)
```

Then, do the following commands
```
sudo docker run --device /dev/fuse/ --cap-add SYS_ADMIN -v /net:/net -v /neuro:/neuro -it new_internship (you bring two volumes net and neuro)
#(you are inside the dock new_internship in root)
# addgroup --gid 1102 fnndsc
# adduser --disabled-password --gecos'' --uid (your ID) --gid 1102 (your username)
# su - (your username) (you access at your local account with the dock)
$ cd /neuro/users/yves.verpillieux (you will see all the folders you are created from your account)
```

# Solve the problem of proxy in the dock
 ```
 sudo docker run --device /dev/fuse/ --cap-add SYS_ADMIN -v /net:/net -v /neuro:/neuro -it new_internship
 # you are inside the dock
 # export http_proxy="http://192.168.13.14:3128"
 # apt-get upgrade
 # apt-get update
 # apt-get install ...
```

# WARNING

Each time you exit the dock you have to commit the dock in order to save what you just installed.
```
sudo docker ps -a
sudo docker commit <ID_container last connexion new_internship> new_internship
```

# Install pydicom for python3
```
git clone https://github.com/darcymason/pydicom.git
cd pydicom
python3 setup.py install
```
Not forget to put the pydicom's folder in the same repository than the program folder

# Install dicom for python3
```
sudo apt-get update
sudo apt-get install python3-dicom
```
