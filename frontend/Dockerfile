# Use the official Node.js image as the base image
FROM node:14

RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash

RUN . ~/.nvm/nvm.sh && \
    nvm install v16.20.2 && \
    nvm use v16.20.2 && \
    npm install -g npm@8.19.4

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json to the container
COPY package.json /app/
COPY package-lock.json /app/

# Install app dependencies
RUN npm install
RUN npm install styled-components

# Copy the entire app to the container
COPY . .

# Build the React app for production
RUN npm run build

# Expose the port that your React app listens on
EXPOSE 3000

# Command to run your app when the container starts
CMD ["npm", "start"]
