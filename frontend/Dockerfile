FROM node:14.16.1-alpine3.13

RUN npm install -g @angular/cli
RUN ng update | awk -v re='@[[:alnum:]]' '$0 ~ re {printf $1 " "}' | xargs ng update --force=true && npm update

RUN addgroup app && adduser -S -G app app
RUN mkdir /app && chown app:app /app
RUN chmod -R 777 /app

USER app
WORKDIR /app

COPY package*.json .    
RUN npm install

COPY . .

EXPOSE 4200

ENTRYPOINT [ "ng", "serve", "--host", "0.0.0.0", "--disable-host-check" ]

