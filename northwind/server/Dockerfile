FROM node:latest

# Set environment variables
ENV APP_ROOT=/app
ENV APP_PORT=3000
ENV DB_HOST=localhost
ENV DB_PORT=3306
ENV DB_USER=root
ENV DB_PASSWORD=changeit

# create the directory and cd into in
WORKDIR ${APP_ROOT}

# copy files into the image
# files will be copied into /app
ADD main.js .
ADD package.json .
ADD public public
ADD views views
ADD config config

# install the dependencies
RUN npm install

## How an image is provision/run
##EXPOSE ${APP_PORT}/udp
EXPOSE ${APP_PORT}

# add healthcheck to the application
HEALTHCHECK --interval=30s --timeout=5s --retries=3 \
   CMD curl -f http://localhost:${APP_PORT}/health > /dev/null || exit 1

# node main.js 3000
# ENTRYPOINT ["node", "main.js"] # default arguments
ENTRYPOINT ["node", "main.js"]
# CMD ["node", "main.js"] # command line arguments overwrites default
# CMD [ "" ] # command line arguments appends
