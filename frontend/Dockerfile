# Build Stage
FROM node:22.14.0-alpine3.21 AS build
WORKDIR /app
COPY package*.json .
RUN npm i && npm cache clean --force
COPY . .
EXPOSE 5173
RUN [ "npm", "run", "build" ]

# Production Stage
FROM nginx:stable-alpine AS production
COPY --from=build /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
