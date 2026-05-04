# DOC-LAB-5
Lab: How Containers Communicate
1. Create Two Containers
```bash
docker run -d -p 1000:80 httpd
```
```bash
docker run -d -p 1010:80 nginx
```
3. Check Running Containers
```bash
docker ps
```
5. Get Container IP
```bash
docker inspect <container-id>
```

👉 Note the IP address (e.g., 172.17.0.3)

4. Enter First Container
```bash
docker exec -it <container-id> /bin/bash
```
6. Install ping inside container
```bash
apt update
```
```bash
apt install iputils-ping -y
```
8. Ping Other Container
```bash
ping <other-container-ip>

```
👉 If replies come → containers are communicating ✅

7. Check Docker Networks
```bash
docker network ls
```
💡 Key Idea
Both containers are on bridge network
They communicate using internal IP

now to install webserver change web page 

1. Update system packages
```bash
apt update
```
3. Install vim (for editing files)
```bash
apt install vim -y
```
5. Go to nginx web directory
```bash
cd /usr/share/nginx/html
```
7. Check existing files
```bash
ls
```
9. Remove default files
```bash   
rm -rf *
```
11. Create a new web page
```bash
vim index.html
```
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
9. Save and exit vim

Press:
```bash
ESC → :wq → Enter
```
10. Restart nginx (to be safe)
```bash
systemctl restart nginx
```
12. Test in browser

Open:
```bash
localhost:hostportnumber
```
-----------------------------------------------------------------------------------------------------------------

if it in apache2

Enter First Container
```bash
docker exec -it <container-id> /bin/bash
```
1. Update system packages
```bash
apt update
```
3. Install vim (for editing files)
```bash
apt install vim -y
```
5. Go to nginx web directory
```bash
cd /usr/local/apache2/htdocs
```
7. Check existing files
```bash
ls
```
you see index.html

7. Remove default files
rm -rf *

8. Create a new web page
vim index.html


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


9. Save and exit vim

Press:
```bash
ESC → :wq → Enter
```
10. Restart nginx (to be safe)
```bash
systemctl restart httpd
```
12. Test in browser

Open:
```bash
localhost:hostportnumber
```

