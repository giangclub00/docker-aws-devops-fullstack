FROM node:14.16.1-alpine3.13

RUN npm install -g ts-node
RUN npm install -g nodemon

RUN addgroup app && adduser -S -G app app
RUN mkdir /app && chown app:app /app
RUN chmod -R 777 /app

USER app
WORKDIR /app

RUN echo -e "DEFAULT_PORT=3000\nDB_CONNECTION_STRING="mongodb://0.0.0.0:27017/tedu-courses"\nDB_NAME="tedu-courses"" > .env
RUN echo -e "DEFAULT_PORT=3000\nDB_CONNECTION_STRING="mongodb://0.0.0.0:27017/tedu-courses"\nDB_NAME="tedu-courses"" > .env.test

COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD [ "npm", "run", "server:dev" ]
