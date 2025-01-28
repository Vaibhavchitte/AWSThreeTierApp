# Stage 1: Build Stage
FROM node:14 AS builder

WORKDIR /app

# Copy package files and install dependencies
COPY package*.json ./

RUN npm install

# Copy the entire source code to the build stage
COPY . .

# If your app has a build step (e.g., React or TypeScript apps), run it here.
# For plain Node.js apps, skip this step or keep it as-is.
# RUN npm run build

# Stage 2: Production Stage
FROM node:14-alpine

WORKDIR /app

# Copy only the necessary files from the build stage
COPY --from=builder /app .

# Set environment to production
ENV NODE_ENV=production

# Expose the application port
EXPOSE 8080

# Start the app
CMD ["node", "index.js"]
