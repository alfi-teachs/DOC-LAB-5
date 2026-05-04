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

now to install webserver change web page 

apt update
apt install vim -y

if nginx web path is  
cd /usr/share/nginx/html
ls
remove all files
rm -rf *
create index.html

```bash
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Docker Bridge Network - AWS</title>
    <style>
        body {
            margin: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background-color: #cce7ff; /* light blue */
            font-family: Arial, sans-serif;
            color: #003366; /* dark blue text */
        }

        .container {
            text-align: center;
            background: white;
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
            max-width: 500px;
        }

        h1 {
            margin-bottom: 15px;
        }

        p {
            font-size: 16px;
        }

        .highlight {
            margin-top: 20px;
            padding: 10px;
            background: #e6f2ff;
            border-radius: 8px;
        }
    </style>
</head>
<body>

<div class="container">
    <h1>AWS Docker Bridge Network</h1>
    <p>
        Containers running on an AWS EC2 instance communicate using the 
        <strong>bridge network</strong>.
    </p>

    <div class="highlight">
        <p>✔ Each container gets its own internal IP</p>
        <p>✔ Containers can ping each other</p>
        <p>✔ Communication happens within the same network</p>
    </div>

    <p style="margin-top:15px;">
        Example: nginx container ↔ httpd container
    </p>
</div>

</body>
</html>


```
copy in browser 
localhost and hostportnumber 
check if u can see web page
-----------------------------------------------------------------------------------------------------------------

if it in apache2

apt update
apt install vim -y

if nginx web path is  
cd /usr/local/apache2/htdocs
ls
remove all files
rm -rf *
create index.html

```bash
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Docker Bridge Network - AWS</title>
    <style>
        body {
            margin: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background-color: orange;
            font-family: Arial, sans-serif;
            color: #003366; /* dark blue text */
        }

        .container {
            text-align: center;
            background: white;
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
            max-width: 500px;
        }

        h1 {
            margin-bottom: 15px;
        }

        p {
            font-size: 16px;
        }

        .highlight {
            margin-top: 20px;
            padding: 10px;
            background: #e6f2ff;
            border-radius: 8px;
        }
    </style>
</head>
<body>

<div class="container">
    <h1>AWS Docker Bridge Network</h1>
    <p>
        Containers running on an AWS EC2 instance communicate using the 
        <strong>bridge network</strong>.
    </p>

    <div class="highlight">
        <p>✔ Each container gets its own internal IP</p>
        <p>✔ Containers can ping each other</p>
        <p>✔ Communication happens within the same network</p>
    </div>

    <p style="margin-top:15px;">
        Example: nginx container ↔ httpd container
    </p>
</div>

</body>
</html>
```


copy in browser 
localhost and hostportnumber 
check if u can see web page


