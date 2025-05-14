# This Dockerfile is for the frontend of a MERN stack application .
# Use the official Node.js image as the base image .

FROM node:20

# Set the working directory in the container to /app
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package.json /app/

RUN npm install

# Copy the rest of the application code to the working directory
COPY . .

# Expose port 5173 for the application
EXPOSE 5173

# Start the application
CMD ["npm", "run", "dev"]

# The application will be available at http://localhost:5173
