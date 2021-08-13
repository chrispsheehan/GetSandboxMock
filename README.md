# GetSandboxMock

Host a sandbox using the opensource code from [getsandbox.com](https://getsandbox.com/)

## Pre-requists

- [docker](https://docs.docker.com/get-docker/)
- [ngrok](https://ngrok.com/download/)
- [jq](https://stedolan.github.io/jq/)

## State

State files are stored in the ./state folder.

## Build docker image

```bash
docker build -t getsandboxlive .
```

## Local

```bash
docker-compose up --force-recreate sandbox
```

```bash
curl http://localhost:8080/hello
```

## Expose to the internet with ngrok

```bash
docker-compose up --force-recreate ngrok
```

```bash
Creating network "getsandboxmock_default" with the default driver
Creating sandbox ... done
Creating sandbox_ngrok ... done
Creating ngrok         ... done
Attaching to ngrok
ngrok            | "https://b864c6591753.ngrok.io"
ngrok exited with code 0
```

```bash
curl https://b864c6591753.ngrok.io/hello
```
