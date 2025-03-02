# Build stage
FROM node:20 AS build-env
WORKDIR /opt/backend
COPY package.json . 
COPY *.js . 
RUN npm install

# Runtime stage (Distroless)
FROM gcr.io/distroless/nodejs20-debian12
WORKDIR /opt/backend
COPY --from=build-env /opt/backend /opt/backend

# Set environment variable
ENV DB_HOST=mysql

# Command to run the application
CMD ["index.js"]
