# DOC-LAB-2
Lab: How Containers Communicate
1. Create Two Containers

docker run -d -p 1000:80 httpd
docker run -d -p 1010:80 nginx

3. Check Running Containers
docker ps

4. Get Container IP
docker inspect <container-id>


👉 Note the IP address (e.g., 172.17.0.3)

4. Enter First Container
docker exec -it <container-id> /bin/bash

5. Install ping inside container
apt update
apt install iputils-ping -y

6. Ping Other Container
ping <other-container-ip>


👉 If replies come → containers are communicating ✅

7. Check Docker Networks
docker network ls

💡 Key Idea
Both containers are on bridge network
They communicate using internal IP
