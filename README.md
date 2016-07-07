# dmd2b-dock
A dock around the dmd2b project.

## Overview
This project consists on creating a dock for the dmd2b project based on the docker technology.

# Get started :

Create an image from Ubuntu dock
```
docker pull Ubuntu
docker ps -a
docker commit <ID_container of Ubuntu> new_internship
```

# Connect to the dock
 ```
 docker run -it new_internship
 # you are inside the dock new_internship in root
 # export http_proxy="http://192.168.13.14:3128"
 # apt-get upgrade
 # apt-get update
 # apt-get install ...
```

## Warning

Each time you exit the dock you have to commit the dock in order to save what you just installed
```
docker ps -a
docker commit <ID_container last connexion new_internship> new_internship
```

# Install pydicom
```
pip install pydicom
  or/and
git clone https://github.com/darcymason/pydicom.git
cd pydicom
python setup.py install
```
