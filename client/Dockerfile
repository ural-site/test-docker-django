FROM node:lts-alpine

# устанавливаем простой HTTP-сервер для статики
RUN npm install -g http-server

# Папка приложения
#ARG APP_DIR=app
#RUN mkdir -p ${APP_DIR}
#WORKDIR ${APP_DIR}

# делаем каталог 'app' текущим рабочим каталогом
WORKDIR /app

COPY ./app/package*.json ./

# устанавливаем зависимости проекта
RUN npm install

COPY ./app .

# собираем приложение для production с минификацией
RUN npm run build

EXPOSE 8080
CMD ["http-server", "dist"]

# docker build --build-arg <build arguments> -t <user-name>/<image-name>:<tag-name> /path/to/Dockerfile
# docker build --build-arg APP_DIR=var/app -t uralsite/node-app:V1 .

# запустим наше приложение Vue.js в контейнере Docker
# docker run -it -p 8080:8080 --rm --name dockerize-vuejs-app-1 vuejs-cookbook/dockerize-vuejs-app
# 
# docker build -t uralsite/vuejs .
# docker run -it -p 8080:8080 --rm --name vuejs uralsite/vuejs