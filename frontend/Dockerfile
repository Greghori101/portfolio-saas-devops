FROM node:22

# Set working directory
WORKDIR /app

# Copy code
COPY ../../portfolio-saas-front /app

# Install dependencies
RUN npm install

# Build app
RUN npm run build

EXPOSE 3000
CMD ["npm", "run", "start"]
