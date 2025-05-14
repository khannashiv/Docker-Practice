# This Dockerfile is for the backend of a MERN stack application .
# Use the official Node.js image as the base image .
FROM node:20

# Set the working directory in the container to /app
WORKDIR /app/

# Copy package.json and package-lock.json to the working directory
COPY package.json /app/

# RUN installs all the dependencies your Node.js app needs inside the Docker image so that the container can run your app properly.
RUN npm install

# Copy the rest of the application code from host to the working directory inside the container .
COPY . .

# Expose port 5050 for the application
EXPOSE 5050

# CMD tells Docker what command to run when the container starts.
CMD ["npm", "start"]

# The application will be available at http://localhost:5050
