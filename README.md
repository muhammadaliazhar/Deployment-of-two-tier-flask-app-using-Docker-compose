# Project-Overview:

In this project our flask app is connected with mysql database. The app allows users to submit messages, which are then stored in the database and displayed on the frontend. We created one container for flask app and 2nd container for mysql-database using docker compose file. Both containers are in the same network so that they can communicate each other. We use docker volume (mysql_data) to protect our mysql-container data. 

# Step: 1
First I create a directory (mysql_data) inside /opt , that I use as a volume in mysql-container. 
```bash
 mkdir /opt/mysql_data
```

# Step: 2
Then git clone the application code in our local system. The below mentioned repo contains code files, Dockerfile and docker-compose file.
```bash
git clone https://github.com/muhammadaliazhar/Deployment-of-two-tier-flask-app-using-Docker-compose.git
cd project-folder
```

# Step: 3
Inside the project folder run the below command, this will build our image from docker file and the creates 2 docker containers, one for app and one for mysql database.
```bash
docker-compose up
Browser url : public-ip:5000
```

![image](https://github.com/user-attachments/assets/9af2c0c6-7f9a-40cf-a867-be1052524ba5)


```bash
Enter some sample data and click on submit button.
```

![image](https://github.com/user-attachments/assets/090f6950-a661-4481-adc5-0effa296c3ee)


Go inside the mysql container using below mention command to check whether the sample data save on mysql database or not.
```bash
docker exec -it mysql /bin/bash
mysql -u root -p
use devops ( this is our database name that we define on compose file)
```
![image](https://github.com/user-attachments/assets/35942fb5-a4a0-4770-84af-b84e56299d8a)

* Here we can see that all the sample data that we submit on our frontend is successfully saved on our mysql database. In this way our frontend app communicates with our mysql database.
  
# Step: 4
Now we delete our conatiners and create conatiners again to check whether our container data persists or not. 
```bash
docker-compose down
docker-compose up -d
```
![image](https://github.com/user-attachments/assets/a6e84555-581f-4c07-b9c9-79fa00053e28)

** Here all our data persists, because we use docker volume so that if our container fails or deleted, our data remains protected due to the use of docker volume.
