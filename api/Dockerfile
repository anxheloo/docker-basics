# First layer is the parent image / environment
FROM node:16-alpine

RUN npm install -g nodemon

# it tells docker that when we run commands, to do it from this working directory
WORKDIR /app

# this is related to the next command
COPY package.json .

 # Before we used npm install after copying the source code in our image, 
 # but now we use it before copying, and we add a copy command above for the package.json only,
 # so we copy package.json first, than we run npm install, and then we copy other source files
 # We use this way in order to cache as much of the commands that are not being changed, so we build our image faster
 RUN npm install

# first dot is the relative path to the directory we want to copy the source files on 
# if source code was on a src directory than it would be ./src
# second dot is the path inside image that we want to copy our sorce code to
COPY . .
#we say copy our source files into our working directory that we have specified called app inside image

# # to specify a command - in our case to install dependencies
# RUN npm install

#  the port is going to be exposed by the container not our pc, cuz we will run the container
EXPOSE 4000
# required for docker desktop port mapping

# when container runs it will run this command that is node app.js
# CMD ["node", "app.js"] without nodemon
CMD ["npm", "run", "dev"]

#After specifying these props, we run in the project directory , docker build -t myapp .      -> myapp is for the name of my app, and since we are in the same directory as the dockerfile , the path is just a dot