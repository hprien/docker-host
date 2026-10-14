# docker-host

## remote-code
### build & start
```sh
sudo docker compose -f remote-code/docker-compose.yml up -d --build
```
### usage
```sh
sudo docker exec -it remote-code bash
happier opencode
```
The login session is persisted in `remote-code/happier-data` (mounted at `/data/happier`, via `HAPPIER_HOME_DIR`) and survives container rebuilds.

## ollama
### login
```sh
sudo docker exec -it ollama bash
ollama login
exit
```
