# dmd2b-dock
Create a dock around the dmd2b project.

## Overview
This project consists on creating a dock for the dmd2b project based on the docker technology.

# Get started :

Create an image from Ubuntu dock.
```
docker pull Ubuntu
docker ps -a
docker commit <ID_container of Ubuntu> new_internship
```
# Bring folders from an outside system inside the dock

The problem with the container is, it is an isolated system so you have to install everything you need and basically the folders you have created with your account.
```
Before you lauch the dock check your ID (uid)

id
uid=20064(yves) gid=1102(grantlab_local) groups=1102(grantlab_local),27(sudo),999(docker)

docker run --device /dev/fuse/ --cap-add SYS_ADMIN -v /net:/net -v /neuro:/neuro -it new_internship (you bring two volumes net and neuro)
# you are inside the dock new_internship in root
# addgroup --gid 1102 fnndsc
# adduser --disabled-password --gecos'' --uid (your ID) --gid 1102 (your username)
# su - (your username) (you access at your local account with the dock)
$ cd /neuro/users/yves.verpillieux (you will see all the folders you are created from your account)
```

# Solve the problem of proxy in the dock
 ```
 docker run --device /dev/fuse/ --cap-add SYS_ADMIN -v /net:/net -v /neuro:/neuro -it new_internship
 # you are inside the dock
 # export http_proxy="http://192.168.13.14:3128"
 # apt-get upgrade
 # apt-get update
 # apt-get install ...
```

# WARNING

Each time you exit the dock you have to commit the dock in order to save what you just installed.
```
docker ps -a
docker commit <ID_container last connexion new_internship> new_internship
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
