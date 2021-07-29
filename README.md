# GetSandboxMock

Host a sandbox locally using the opensource code from [getsandbox.com](https://getsandbox.com/)

## Pre-requists

- [docker](https://docs.docker.com/get-docker/)
- [ngrok](https://ngrok.com/download/)
- [jq](https://stedolan.github.io/jq/)

## Run Sandbox locally

```bash
Run Sandbox
```

- This will show any errors/info in the terminal

```bash
docker run -p 8080:8080 -v $(pwd)/src:/base -it getsandbox/worker-cli:latest
```

Test

```bash
http://localhost:8080/hello
```

Expose

```bash
ngrok http 8080
```

Get ngrok url

```bash
curl -s http://localhost:4040/api/tunnels | jq '.tunnels[0].public_url'
```

## Ngrok on Docker

```bash
docker rm sandbox -f
docker run -d -p 8080:8080 --name sandbox -v $(pwd)/src:/base getsandbox/worker-cli:latest
docker rm sandbox_ngrok -f
docker run -d -p 4040 --name sandbox_ngrok -it --link sandbox wernight/ngrok ngrok http sandbox:8080
curl $(docker port sandbox_ngrok 4040)/api/tunnels
```

## Docker compose

```bash
docker build -t getsandboxlive .
docker-compose up
```

Url displayed in output as below

```bash
jq_processor     | "http://f0afab9ae1f9.ngrok.io"
```

Activity log

```bash
http://127.0.0.1:8090/
```
