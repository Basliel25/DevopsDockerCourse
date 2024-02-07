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
