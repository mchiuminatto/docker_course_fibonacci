# build stage 
FROM node:16-alpine as builder
WORKDIR "/app"
COPY ./package.json ./
RUN npm install
COPY . .

# nginx setup stage
FROM nginx

# expose the port nginx will listen to
EXPOSE 3000

COPY ./nginx/default.conf /etc/nginx/conf.d/default.com

# copy the resultant file from builder stage to the folder where nginx will serve
COPY --from=builder /app/build /usr/share/nginx/html