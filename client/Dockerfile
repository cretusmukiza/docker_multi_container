# Load base image
FROM node:alpine as builder

# Set work directory
WORKDIR /app

#Copy package.json
COPY ./package*.json ./

#Install package
RUN npm install

#Copy other file
COPY ./ ./

#Build the production version
RUN npm run build


#Load nginx
FROM nginx

#Listen on port
EXPOSE 80

#Copy conf file
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

#Copy build to nginx
COPY --from=builder app/build /usr/share/nginx/html

