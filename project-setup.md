# $\color{orange} \textbf {Project Setup} $
# Launch EC2 instance
   - OS : ubuntu
   - instance type : t3.medium
   - security group : allow following ports
      - port no :22 (SSH)
      - port no : 80 (http)
      - port no : 8080 (Tomcat)
      - port no : 3306 (MYSQL/Arora )
   - storage : 30 GB
- Connect the instance.
---
- install Git
```
apt install git -y
```
- install Dcoker
```
apt-get update
apt-get install docker.io -y
systemctl start docker
usermod -aG docker ubuntu
newgrp docker
chmod 777 /var/run/docker.sock
```
---
## Clone the Repository
```
git clone https://github.com/abhipraydhoble/ThreeTier-Using-Docker.git
cd ThreeTier-Using-Docker
```
---
## Setup the Database
- Navigate to the Database repository
```
cd Database
```
- **The SQL script creates a studentapp database and a students table with student details.**
- The Dockerfile:
- Uses the MariaDB base image.
- Sets the root password (1234).
- Copies student-rds.sql into the container for automatic database initialization.
- Starts the MariaDB service (mariadbd).
## Build the MySQL Docker Image
```
docker build -t my-mysql-db .
```
```
docker images
```
## Run the MySQL Container
```
docker run -d --name my-mysql-container -p 3306:3306 my-mysql-db
```
```
docker ps
```
- **Copy this IP address for the next step.**
---
## Configure Backend
- Navigate to the backend directory
```
cd ../Backend
```
## Update Context.xml file
- Edit ``context.xml`` file and replace ``<MYSQL_Container_IP>`` with actual MYSQL container IP that we copied in previous step.
```
<Context>
    <Resource name="jdbc/StudentDB" auth="Container"
        type="javax.sql.DataSource" driverClassName="com.mysql.cj.jdbc.Driver"
        url="jdbc:mysql://<MYSQL_CONTAINER_IP>:3306/studentdb"
        username="root" password="root" maxTotal="10" maxIdle="5"/>
</Context>
```
##  Build the Backend Image
```
docker build -t my-backend-app .
```
```
docker images
```
##  Run the Backend Container
```
docker run -d --name my-backend-container -p 8080:8080 my-backend-app
```
##  Verify Backend
- Check if the backend is working properly:
```
curl http://<INSTANCE_PUBLIC_IP>:8080/student
```
- **Replace ``<INSTANCE_PUBLIC_IP>`` with your server's public IP.**
---
## Configure and Run the Frontend
- Navigate to the ``frontend`` directory:
```
cd ../Frontend
```
## Update the ``index.html`` File in Frontend Directory
- Edit ``index.html`` and replace the backend URL at line 122:
```
<a href="http://<INSTANCE_PUBLIC_IP>:8080/student/">Register Here</a>
```
- **Replace <INSTANCE_PUBLIC_IP> with your actual server's public IP.**
##  Build the Frontend Image
```
docker build -t my-frontend-app .
```
```
docker images
```
## Run the Frontend Container
```
docker run -d --name my-frontend-container -p 80:80 my-frontend-app
```
```
docker ps
```
---
## Access the Final Application
- Now, open your browser and go to:
```
http://<INSTANCE_PUBLIC_IP>
```
## You should see the final application running!
![Screenshot 2025-06-27 125514](https://github.com/user-attachments/assets/4de2f6a6-411f-485d-a2a7-6c021e4a6022)
![Screenshot 2025-06-27 125611](https://github.com/user-attachments/assets/f1c9ce07-5fca-4255-b571-1da229cda9a0)
![Screenshot 2025-06-27 125747](https://github.com/user-attachments/assets/f4aed6e4-f31a-4555-8199-474232f9aac6)




