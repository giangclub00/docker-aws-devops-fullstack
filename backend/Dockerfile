FROM node:14.16.1-alpine3.13
RUN npm install -g ts-node
RUN addgroup app && adduser -S -G app app
RUN mkdir /app && chown app:app /app
RUN chmod -R 777 /app
USER app
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD [ "npm", "run", "server:dev" ]
