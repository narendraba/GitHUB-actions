# Stage 1: Build the application
FROM node:14-alpine AS builder

WORKDIR /usr/src/app

COPY package*.json ./
RUN npm install

COPY . .
# Assuming you have a build step, e.g., for TypeScript or bundling
# RUN npm run build

# Stage 2: Create the final image
FROM node:14-alpine

WORKDIR /usr/src/app

COPY --from=builder /usr/src/app ./

# Install only production dependencies
RUN npm install --production

EXPOSE 3001

CMD ["node", "appointment-service.js"]

