# GetSandboxMock

Host a sandbox locally using the opensource code from [getsandbox.com](https://getsandbox.com/)

## Pre-requists

- [Install docker](https://docs.docker.com/get-docker/)
- [Install ngrok](https://ngrok.com/download/)

## Run Sandbox locally

This will show any errors/info in the terminal

```bash
docker run -p 8080:8080 -v $(pwd)/src:/base -it getsandbox/worker-cli:latest
```

## LocalHost

Ngrok dashboard

```bash
http://localhost:4040
```

Sandbox endpoints

```bash
http://localhost:8080/hello
```

## Expose localhost

```bash
ngrok http 8080
```

## Host ngrok on Docker

Run Sandbox in docker manually.

```bash
docker rm sandbox -f
docker run -d -p 8080:8080 --name sandbox -v $(pwd)/src:/base getsandbox/worker-cli:latest
docker rm sandbox_ngrok -f
docker run -d -p 4040 --name sandbox_ngrok -it --link sandbox wernight/ngrok ngrok http sandbox:8080
curl $(docker port sandbox_ngrok 4040)/api/tunnels
```

Docker compose

```bash
docker-compose up
curl $(docker port sandbox_ngrok 4040)/api/tunnels
```

## [jq](https://stedolan.github.io/jq/)

(curl $(docker port sandbox_ngrok 4040)/api/tunnels) | jq -c '.tunnels[] | select(.proto | contains("https"))? | .public_url'
