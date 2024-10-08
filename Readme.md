## Docker project 2

# Creating a Dockerfile to Build and Deploy a Web Application
Objective: Write a Dockerfile to create an image for a simple web application and run it as a container.
Steps:
 1. Create a Project Directory:

mkdir Docker_Project
cd Docker-Project 
 2. Create a Simple Web Application:

Save this file in the Docker_Project directory.
 3. Write the Dockerfile:
Create a Dockerfile in the Docker_Project directory with the following content:
 ![img-1](<Screenshot from 2024-10-07 16-06-29.png>)
# Use the official Nginx base image
FROM nginx:latest

# Copy the custom HTML file to the appropriate location
COPY index.html /usr/share/nginx/html/

# Expose port 80
EXPOSE 80
        ◦ 
Build the Docker Image:

docker build -t my-devops-image .
![img- 2](<Screenshot from 2024-10-07 16-09-29.png>)
 4. Run a Container from the Built Image:

docker run --name my-devops-container -d -p 3000:80 my-devops-image
![img- 3](<Screenshot from 2024-10-07 16-10-01.png>)    
 5. Verify the Web Application:
        ◦ Visit http://localhost:3000/ in your browser. You should see your custom web application.
## Modifying the Container and Creating a New Image
Objective: Modify the running devops container to serve a custom HTML page and create a new image from this modified container.
Steps:
Access the Running Container:

docker exec -it my-devops-image /bin/bash
![img- 4](<Screenshot from 2024-10-07 16-10-33.png>)
 1. Create a Custom HTML Page:

![img-5](<Screenshot from 2024-10-07 15-19-33.png>)
 2. Exit the Container:

exit

 3. Commit the Changes to Create a New Image:

docker commit my-custom-container

![img- 6](<Screenshot from 2024-10-07 16-12-12.png>)

4. Run a Container from the Built Image:

docker run --name my-custom-devops-container -d -p 3000:80 my-custom-container
![img- 7](<Screenshot from 2024-10-07 16-12-54.png>)

#    5. Verify the New Container:
        ◦ Visit http://localhost:3000 in your browser. You should see your custom HTML page.
![img-8](<Screenshot from 2024-10-07 17-48-21.png>)