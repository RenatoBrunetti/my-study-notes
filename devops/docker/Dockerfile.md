# Dockerfile
[main](../../README.md) | [devops](../README.md) | [docker](README.md) | [dockerfile](Dockerfile.md)

> if some instruction changes after building execution, the cache will be ignored from the changed line until the end.

> if some instruction needs another one, run both in the same run command.

<br>

## Samples:

### Create an Ubuntu with Curl image.

```Dockerfile
# Dockerfile
FROM ubuntu
RUN apt update
RUN apt install curl --yes
RUN apt install vim --yes

# Or
FROM ubuntu
RUN apt update && \
  apt install curl --yes && \
  apt install vim --yes

# Or
FROM ubuntu
RUN apt update && \
  apt install curl vim --yes
```

```sh
docker build -t ubuntu-curl .
```
