# httpd-docker

## Build

```
docker build -t drewkerrigan/httpd .
```

## Run

```
docker run -p 8000:8000 drewkerrigan/httpd /start 8000
```

## Test

```
curl http://127.0.0.1:8000
```

## Marathon Usage Example

```
{
    "id": "/svc",
    "cmd": "/start $PORT0",
    "instances": 1,
    "cpus": 0.1,
    "mem": 32,
    "container": {
        "type": "DOCKER",
        "docker": {
            "image": "drewkerrigan/httpd"
        }
    },
    "portDefinitions": [
        {
            "name": "web",
            "protocol": "tcp",
            "port": 0
        }
    ],
    "healthChecks": [
        {
            "portIndex": 0,
            "path": "/",
            "protocol": "HTTP"
        }
    ]
}
```
