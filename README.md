# Real World Project: Database Shard Github
```
This project done on a Ubuntu virtual machine 20.10.

Thanks to Luma for helping me to complete this project
```

## The requirements:
```
Build an app in docker-compos after installing Docker, docker compose, and Mariadb.
Set up a sharded database.
Demonstrate the merged database.
```
 
## To install Docker:


### Update your existing list of packages:
```
sudo apt update   
```

### Install a few prerequisite packages which let apt use packages over HTTPS
```
sudo apt install apt-transport-https ca-certificates curl software-properties-common 
```

### Then add the GPG key for the official Docker repository to your system
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

### Add the Docker repository to APT sources
```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"    
```

### Update the package database with the Docker packages from the newly added repo
```
sudo apt update    
```

### Make sure you are about to install from the Docker repo instead of the default Ubuntu repo
```
apt-cache policy docker-ce
```

### Install Docker
```
sudo apt install docker-ce   
```

### To check the Docker status
```
sudo systemctl status docker 
```

## To install Docker Compose:
```
sudo apt install docker-compose
```
## To install Mariadb:
```
sudo apt install mariadb-client
```
### Cloning this maxscale-docker repository by running this command on the terminal.
```
git clone https://github.com/AhmedAlkhafai99/maxscale-docker
```
#### Then move to maxscale-docker/maxscale/ directory:
```
cd maxscale-docker/maxscale/
```
### To bring the containers up:
```
docker-compose up -d
```

### It will show this result
```
Starting maxscale_master2_1 ... done
Starting maxscale_master_1  ... done
Starting maxscale_maxscale_1 ... done
```

### Now you should have 3 containers maxscale_master2_1, maxscale_master_1 and maxscale_maxscale_1 by running this command 
```
docker-compose ps

      Name                   Command            State            Ports         
--------------------------------------------------------------------------------
maxscale_master2_1    docker-entrypoint.sh       Up      0.0.0.0:4003->3306/tcp 
                      mysql ...                                                 
maxscale_master_1     docker-entrypoint.sh       Up      0.0.0.0:4001->3306/tcp 
                      mysql ...                                                 
maxscale_maxscale_1   /usr/bin/tini -- docker-   Up      3306/tcp, 0.0.0.0:4000->4000/tcp, 0.0.0.0:8989->8989/tcp                              
```                                                          





maxscale_master2_1    docker-entrypoint.sh mysql ...   Up      0.0.0.0:4003->3306/tcp                                  
maxscale_master_1     docker-entrypoint.sh mysql ...   Up      0.0.0.0:4001->3306/tcp                                  
maxscale_maxscale_1   /usr/bin/tini -- docker-en ...   Up      3306/tcp, 0.0.0.0:4000->4000/tcp, 0.0.0.0:8989->8989/tcp

```
### Run this command to check that the servers up and running
```
docker-compose exec maxscale maxctrl list servers
