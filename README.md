# docker-host

## remote-code
### build & start
```sh
sudo docker compose -f remote-code/docker-compose.yml up -d --build
```
### usage
```sh
sudo docker exec -it remote-code bash
happier auth login
```

## ollama
### login
```sh
sudo docker exec -it ollama bash
ollama login
exit
```
