FROM node:14.16.1-alpine3.13

RUN npm install -g @angular/cli@11.2.12
RUN npm uninstall @angular-devkit/build-angular
RUN npm install --save-dev @angular-devkit/build-angular

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

