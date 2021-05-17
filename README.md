# push-notification-test

Testing the [Notification API](https://developer.mozilla.org/en-US/docs/Web/API/notification)

## Development

1. Rename, and change the _env var file_ if necessary

        ```bash
        mv .env.example .env
        ```

2. Init the service and install the dependencies

    * Init the service

    ```bash
    docker-compose run --rm --service-ports pn bash
    ```

    * Install the dependencies

    ```bash
    yarn
    ```

3. Init the local server at [localhost:8080](http://localhost:8080)

    ```bash
    docker-compose up pn
    ```
