# Use an official Node.js runtime as a parent image
FROM node:14 as build

# Set the working directory within the container
WORKDIR /app

# Copy package.json and package-lock.json to the container
COPY package*.json ./

# Install application dependencies
RUN npm install

# Copy the rest of your application code to the container
COPY . .

# Build your React application
RUN npm run build

# Use a smaller, production-ready Node.js image for the final image
FROM node:14

# Set the working directory within the container
WORKDIR /app

# Copy the built React application from the previous stage
COPY --from=build /app/build ./build

# Expose the port your React application will run on (e.g., 3000)
EXPOSE 3000

# Define the command to start your React application
CMD ["npx", "serve", "-s", "build"]