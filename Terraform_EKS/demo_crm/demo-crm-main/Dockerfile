# Base image lightweight version of Node.js
FROM node:18-alpine

# Run update and
RUN apk update && apk add --no-cache yarn

# Set environment to production (before installing dependencies)
#ENV NODE_ENV production

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
