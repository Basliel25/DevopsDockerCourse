# Devops with Docker (Proposed Solutions)

## 1.9
___
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
___
Submit the command you used to complete the exercise

```Shell
docker run -it -d -p 8080:8080 --name mappedServer devopsdockeruh/simple-web-service:v3 
```