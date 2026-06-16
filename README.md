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

## OGC Compliance Testing (TEAM Engine)

You can test the compatibility of the OGC API Features and OGC API Tiles endpoints using the OGC TEAM Engine.

### 1. Manual Configuration

To ensure the test containers can correctly follow the links in the API responses, update your configuration:

*   **Update `.env`**: Change `HOST_URL` to `http://httpd`.
    ```env
    HOST_URL=http://httpd
    ```
*   **Update `/etc/hosts`**: Add the following line to your host machine's `/etc/hosts` file:
    ```text
    127.0.0.1 httpd
    ```

### 2. Running the Test Suites

1.  **Start the main stack**:
    ```bash
    docker compose up -d
    ```
2.  **Start the test stack**:
    ```bash
    docker compose -f docker-compose.test.yml up -d
    ```
3.  **There are two different instances, one for each test suite**:
    *   **OGC API Features 1.0**: [http://localhost:8082/teamengine/](http://localhost:8082/teamengine/)
    *   **OGC API Tiles 1.0**: [http://localhost:8083/teamengine/](http://localhost:8083/teamengine/)
4.  **To login**: Use `ogctest` for both username and password.
5.  **Example configurations**: 

**OGC API Features 1.0**
![features example configuration](features.png)

**OGC API Tiles 1.0**
![tiles example configuration](tiles.png)


## License

This project is released under an [MIT License](./LICENSE)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
