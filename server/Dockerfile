# Use an official Node.js runtime as a parent image
FROM node:14

# Set the working directory within the container
WORKDIR /usr/src/app

# Copy package.json and package-lock.json to the container
COPY package*.json ./

# Install application dependencies
RUN npm install

# Copy the rest of your application code to the container
COPY . .

# Expose the port your application will run on (e.g., 3001)
EXPOSE 3001

# Define the command to start your Node.js application
CMD ["node", "app.js"]
