# CITE OCG API

## Quick Setup

You will need `docker` and `docker-compose` installed in your system, in order to run this infrastructure. 

## Start pygeoapi

Type:

```
docker compose up
```

Or, if you want to run it in the background

```
docker compose up -d
```


## Environment Variables

This compositions read secrets from an environment file on this folder: ```.env```.

Create this file with the following format, replacing "REMOTE_TEST_PASSWORD=postgres" by a reasonable value.

```
PYGEOAPI_OPENAPI_GENERATE_FAIL_ON_INVALID_COLLECTION=false
CONTAINER_PORT=80
HOST_URL=http://localhost
REMOTE_TEST_HOST="postgis"
REMOTE_TEST_PORT="5432"
REMOTE_TEST_DB="geodb"
REMOTE_TEST_USER="postgres"
REMOTE_TEST_PASSWORD="postgres"
REMOTE_TEST_URL=postgresql://postgres:postgres@postgis:5432/geodb
```

## License

This project is released under an [MIT License](./LICENSE)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
