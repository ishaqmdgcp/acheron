#BASE IMAGE - BUILDER
FROM node:11-alpine AS builder

#COPY FILES
COPY . ./angular-example-app

#SWITCH TO WORKING DIRECTORY
WORKDIR /angular-example-app

#INSTALL DEPENDENCIES
RUN npm install

#RUN NODE BUILD
RUN npm run build:prod:en


#BASE IMAGE - DEPLOYER
FROM nginx:1-alpine

#COPY FROM BUILDER
COPY --from=builder /angular-example-app/dist/browser/ /usr/share/nginx/html

#EXPOSE PORT
EXPOSE 80

#RUN WEBSERVER
CMD ["nginx", "-g", "daemon off;"]

