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

# Create a non-root user and group
#RUN addgroup --system --gid 1001 nodejs && adduser --system --uid 1001 nextjs

# Change ownership of the project directory
#RUN chown -R nextjs:nodejs /project/demo-crm/

# Switch to the non-root user	
#USER nextjs

# Expose application port
EXPOSE 3000

# Run the development server
CMD ["yarn", "run", "dev"]



