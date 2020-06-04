# :rocket: Docker

## first-build
```bash
docker image build -t ex-simple-build .

docker image ls

docker container run -p 80:80 ex-simple-build
```
## build-with-args
```bash
docker image build -t ex-build-arg .

docker image build --build-arg S3_BUCKET=myapp -t ex-build-arg .

-- Buscar dado especifico dentro da image
docker image inspect --format="{{index .Config.Labels \"maintainer\"}}" ex-build-arg
```
## build-with-copy
```bash
docker image build -t ex-build-copy .

docker container run -p 80:80 ex-build-copy
```
## build-dev
```bash
docker image build -t ex-build-dev

docker container run -it -v $(pwd):/app -p 80:8000 --name python-server ex-build-dev

- acessando dado dentro de outro container

docker container run -it --volumes-from=python-server debian cat /log/http-server.log

- Subindo image para Docker Hub
docker image tag ex-simple-build docker/simple-build:1.0
docker login --name=yourlogin
docker image push docker/simple-build:1.0

```