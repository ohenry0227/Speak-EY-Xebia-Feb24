Create a Network:

docker network create --driver bridge spark-net 

Download centos image and create a container

docker run -it --name spark0 --hostname spark0 --privileged -p 8080:8080 -p 7077:7077 -p 4040:4040 -p 8081:8081 -p 8090:8090   --network spark-net centos  /usr/sbin/init 

Bind container to a network

docker network connect spark-net spark0 

To Start container:

docker start  spark0 

To copy a file from local to a container

docker cp  [local file name] spark0:/opt

Connect to a container

docker exec -it  spark0 /usr/bin/bash 


docker run -dit  --name spark1 -p 8082:8081  -p 4041:4040 --network spark-net  --entrypoint /bin/bash centos


docker network inspect spark-net 
