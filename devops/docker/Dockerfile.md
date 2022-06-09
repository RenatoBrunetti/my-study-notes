# Dockerfile
[main](../../README.md) | [devops](../README.md) | [docker](README.md) | [dockerfile](Dockerfile.md)

> if some instruction changes after building execution, the cache will be ignored from the changed line until the end.

<br>

## Samples:

### Create an Ubuntu with Curl image.

```Dockerfile
# Dockerfile
FROM ubuntu
RUN apt update
RUN apt install curl --yes
```

```sh
docker build -t ubuntu-curl .
```
