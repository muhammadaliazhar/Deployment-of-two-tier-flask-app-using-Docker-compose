Deployment of a two-tier-Flask-App-using Docker-compose

Project-Overview:
In this project our flask app is connected with mysql database. The app allows users to submit messages, which are then stored in the database and displayed on the frontend. We created one container for flask app and 2nd container for mysql-database using docker compose file. Both containers are in the same network so that they can communicate each other. We use docker volume (mysql_data) to protect our mysql-container data. 
Step: 1
First I create a directory (mysql_data) inside /opt , that I use as a volume in mysql-container. 
# mkdir /opt/mysql_data
Step: 2
Then git clone the application code in our local system. The below mentioned repo contains code files, Dockerfile and docker-compose file.
# git clone https://github.com/muhammadaliazhar/Deployment-of-two-tier-flask-app-using-Docker-compose.git
# cd project-folder
Step: 3
Inside the project folder run the below command, this will build our image from docker file and the creates 2 docker containers, one for app and one for mysql database.
# docker-compose up
Browser url : public-ip:5000
Enter some sample data and click on submit button.
Go inside the mysql container using below mention command to check whether the sample data save on mysql database or not.
# docker exec -it mysql /bin/bash
# mysql -u root -p
# use devops ( this is our database name that we define on compose file)
* Here we can see that all the sample data that we submit on our frontend is successfully saved on our mysql database. In this way our frontend app communicates with our mysql database.
Step: 4
Now we delete our conatiners and create conatiners again to check whether our container data persists or not. 
# docker-compose down
# docker-compose up -d
** Here all our data persists, because we use docker volume so that if our container fails or deleted, our data remains protected due to the use of docker volume.
