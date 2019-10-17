# Bonita mockServer

Utility project to setup quickly a mock server. Allow to mock external REST API.

Based on [mockServer](http://www.mock-server.com/), using its docker distribution.

## Build

```shell script
# may require `sudo` depends on yous docker setting
docker build -t bonita-mock-server .
```

## Configure responses

Edit [initializerJson.json](data/initializerJson.json) file. many examples available on [mockerServer documentation](http://www.mock-server.com/mock_server/creating_expectations.html)


## Run

```shell script
# may require `sudo` depends on yous docker setting
docker run -d \
 --name mockserver \
 -p 1080:1080 \
 bonita-mock-server \
 -serverPort 1080 \
 -jvmOptions -Dmockserver.initializationJsonPath="/data/initializerJson.json"
```

# Test

```shell script
curl http://localhost:1080/ping/127.0.0.1
```
Response
```json
{
"method": "GET",
"path": "/ping/127.0.0.1"
}
```

## Check logs

```shell script
# may require `sudo` depends on yous docker setting
docker logs mockserver
```
