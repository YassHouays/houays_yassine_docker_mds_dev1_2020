# houays_yassine_docker_mds_dev1_2020
# docker project
This is a school project, the goal : create a docker-compose and dockerFile to run our API project
### INSTALLATION
Download this project with git clone : ``` git clone https://github.com/YassHouays/houays_yassine_docker_mds_dev1_2020 ``` </Br>
And start it with ``` docker-compose up --build  ```

### STRUCTURE
You will find one DockerFile in the backend of the project and one on the Frontend
In the main repository a Docker-compose , ready to start everything.

### DOCKERFILE Content
```
FROM xxxx : Our image version

# Create a directory where our app will be placed
RUN mkdir -p /usr/src/app

# Change directory so that our commands run inside this new directory
WORKDIR /usr/src/app

# Copy dependency definitions
COPY package*.json /usr/src/app/

# Install dependecies
RUN npm install

# Get all the code needed to run the app
COPY . /usr/src/app/

# Expose the port the app runs in
EXPOSE 3000

# Run the app
CMD ["npm", "start"]
```

### DOCKER-COMPOSE Content

# The version of the compose file format.
version : '3'

# List of our services

services : 

# Configuration options that are applied at build time.

  backend :
    build : backend 
    ports: 
      - 8080:8080
    
  frontend :
    build : frontend
    ports : 
      - 3000:3000

  mongodb : 
    image : mongo:latest
    restart : always
    container_name : mongodb 
    ports : 
      - 27017:27017