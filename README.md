# Devops with Docker (Proposed Solutions)

## 1.9
Submit the command you used to complete the exercise

**Command**
```bash
mkdir tmp && cd tmp && touch log.txt

docker run --mount type=bind,source="$(pwd)"/tmp/log.txt,target=/usr/app/logs.txt devopsdockeruh/first_volume_exercise
```

**Result**
```console
Secret message is:
"Volume bind mount is easy."
```

## 1.10
Submit the command you used to complete the exercise

```Shell
docker run -it -d -p 8080:8080 --name mappedServer devopsdockeruh/simple-web-service:v3 
```

## 1.11
Submit the command you used to complete the exercise
```Dockerfile
FROM openjdk:8

WORKDIR /usr/src

COPY . .

ENTRYPOINT ["./mvnw package"]

RUN ava -jar ./target/docker-example-1.1.3.jar

EXPOSE 8080
```

Shell
```sh
docker build . -t spring-App
docker run -p 8080:8080 spring-App
```

## 1.12
```Dockerfile
FROM archlinux

WORKDIR

COPY . .

RUN pacman -Syu && pacman -S nodejs npm
RUN npm install -g serve

CMD [""npx", "serve", "-s", "-l", "5000", "build"]

EXPOSE 5000
```

```sh
    docker build . -t example-frontend
    docker run -p 5000:5000 example-frontend
```

## 1.13
```Dockerfile
FROM archlinux

WORKDIR /usr/src

COPY . .

RUN pacman -Syu && pacman -S go

ENV PATH /usr/local/go/bin:$PATH

RUN go build

RUN go test

CMD ./server

EXPOSE 8080
```

## 1.14
**Dockerfile(frontend)**
```Dockerfile
FROM archlinux

WORKDIR

COPY . .

ENV REACT_APP_BACKEND_URL http://localhost:8080/

RUN pacman -Syu && pacman -S nodejs npm
RUN npm install -g serve

CMD [""npx", "serve", "-s", "-l", "5000", "build"]

EXPOSE 5000
```

**Dockerfile(Backend)**
```Dockerfile
FROM archlinux

WORKDIR /usr/src

COPY . .

RUN pacman -Syu && pacman -S go

ENV PATH /usr/local/go/bin:$PATH
ENV REQUEST_ORIGIN http://localhost:5000

RUN go build
RUN go test

CMD ./server

EXPOSE 8080
```
**Shell commands**
```sh
docker build . -t example-backend
docker run -d -p 8080:8080 example-backend

docker build . -t example-frontend
docker run -d -p 5000:5000 example-frontend
```