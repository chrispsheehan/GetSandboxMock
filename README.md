# GetSandboxMock

Host a sandbox locally using the opensource code from [getsandbox.com](https://getsandbox.com/)

## Pre-requists

- [Install docker](https://docs.docker.com/get-docker/)
- [Install ngrok](https://ngrok.com/download/)

## Run locally

```bash
docker run -p 8080:8080 -v $(pwd)/src:/base -it getsandbox/worker-cli:latest
```

## Access locally

```bash
http://127.0.0.1:8080/hello
```

Any traffic or errors are displayed in the terminal.

```shell
<< Status: 200 (processing 1ms wallclock 1ms)
<< Headers: {Access-Control-Allow-Origin=*, Access-Control-Allow-Methods=GET,POST,PUT,DELETE,PATCH,OPTIONS, Access-Control-Allow-Credentials=true, Access-Control-Allow-Headers=Content-Type, Content-Type=text/plain}
<< Body: 'Hello world'
** Error processing request for GET /favicon.ico - Invalid route
** Error processing request for GET / - Invalid route
```

## Access externally

- [Install ngrok](https://ngrok.com/download/)

```bash
ngrok http 8080
```

In this case the mock instance is accessed via <http://c4413b4c3205.ngrok.io>

```bash
ngrok by @inconshreveable                                                                                (Ctrl+C to quit)
Session Status                online                                                                                     
Session Expires               1 hour, 54 minutes                                                                         
Update                        update available (version 2.3.40, Ctrl-U to update)                                        
Version                       2.3.35                                                                                     
Region                        United States (us)                                                                         
Web Interface                 http://127.0.0.1:4040                                                                      
Forwarding                    http://c4413b4c3205.ngrok.io -> http://localhost:8080                                      
Forwarding                    https://c4413b4c3205.ngrok.io -> http://localhost:8080                                     
```
