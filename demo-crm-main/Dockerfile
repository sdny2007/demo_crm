# Base image lightweight version of Node.js
FROM node:18-alpine

# Run update and install yarn
RUN apk update && apk add --no-cache yarn

# Set the MongoDB URI environment variable
ENV MONGODB_URI="mongodb://user:pass@mongo-db:27017/customers?authSource=admin"

# Set working directory
WORKDIR /project/demo-crm/

# Copy project files
COPY . .

# Install dependencies using Yarn
RUN yarn install --frozen-lockfile

# Build the Next.js application
RUN yarn build

# Expose application port
EXPOSE 3000

# Run the development server
CMD ["yarn", "run", "dev"]




