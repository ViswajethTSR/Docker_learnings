# Docker Learnings

## Basics
 
**docker ps = list container**

**docker ps -a= list all container**

**docker images = list images**

**docker volume = list volume**

**docker rmi=remove image**

**docker rm=remove container**

**docker exec -it = to handle the container** 

## Create image

**docker bulid -t <image_name> .**

## Deploy the image by specifing the container name with port binding

**docker run -p <port_no> : <port_no> --name <container_name> <image_name>** 

# Pulling the image from the docker environment

## Mongodb

**docker pull mongo**

**docker volume create <Volume_name>**

**docker run --name <Container_Name> -d -p 27017:27017 -v <Volume_name>:/data/db mongo**

**docker exec -it <Container_Name> bash =to access the Container's bash**

### The following command backup the collection of the atlas mongodb in the path we have mentioned 

**docker exec -it <Container_name> bash**

**mongodump --uri "mongodb+srv://< username >:< password > @cluster0.qpdcsrl.mongodb.net/< Collection_name > ?retryWrites=true&w=majority" --out /data/db/**


### THe following command restore the backup file in the volume

**docker exec -it Users mongorestore --db task /data/db/task/gpsdata.bson**

#### To check

**docker exec -it <Container_name> bash**

**Users> mongosh** // enter the shell

**test> show dbs** //Returns the database

**users> show collections** //Returns the collections

**users> db.collectionname.find()** // Returns all the documetns in the collections