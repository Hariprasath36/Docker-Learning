# Inherit from a base Node.js image
FROM node:20-alpine3.18

# Create a non-root user and group
RUN addgroup app && adduser -S -G app app

# Set the working directory and assign ownership to the non-root user
WORKDIR /app
COPY package*.json ./

# Install dependencies as root
USER root
RUN npm install

# Change ownership of the /app directory to the app user
RUN chown -R app:app /app

# Copy the remaining files and ensure they are owned by the app user
COPY . .
RUN chown -R app:app /app

# Switch to the non-root user
USER app

# Expose the port and run the application
EXPOSE 3000
CMD ["npm", "run", "dev"]
