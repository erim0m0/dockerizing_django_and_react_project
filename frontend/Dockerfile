# Build Stage
FROM node:22.14.0-alpine3.21 AS build
WORKDIR /app
COPY package*.json .
RUN npm i
COPY . .
EXPOSE 5173
CMD [ "npm", "run", "build" ]

# Production Stage
FROM nginx:stable-alpine AS production
COPY --from=build /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

