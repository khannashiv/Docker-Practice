# This Dockerfile is for the frontend of a MERN stack application .
# Use the official Node.js image as the base image .
FROM node:20

# Set the working directory in the container to /app
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package.json /app/

# RUN installs all the dependencies your Node.js app needs inside the Docker image so that the container can run your app properly.
RUN npm install

# Copy the rest of the application code from host to the working directory inside the container .
COPY . .

# Expose port 5173 for the application
EXPOSE 5173

# CMD tells Docker what command to run when the container starts.
CMD ["npm", "run", "dev"]

# The application will be available at http://localhost:5173



# More details about the RUN npm install command:

        # RUN npm install .

                    # Here's what it does during Docker image build:

                        # Reads package.json.
                        # It checks what libraries (e.g., Express, React, etc.) your app depends on.

                    # Downloads the dependencies:
                        # It installs those libraries into the node_modules directory inside the container's filesystem.
                        # Makes dependencies available for app execution:
                        # When the container starts, all required code is already present.

