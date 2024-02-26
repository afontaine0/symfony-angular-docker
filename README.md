# Demo Symfony + MySQL + Docker

## Prerequisites

- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

## Installation

1. Clone the repository

    ```bash
    git clone <repository-url> --recurse-submodules
    ```

    > [!WARNING]
    > We use submodules to include the Symfony Demo application. That's why we need to use the `--recurse-submodules` flag to clone the repository and the Symfony Demo application.

2. Build and start the project

    ```bash
    docker-compose up -d
    ```

3. The application is now running on [http://localhost:3000](http://localhost:3000)

    > [!NOTE]
    > You may need to wait a few seconds for the application to start.

## What's included

### Symfony

The Symfony application is the official [Symfony Demo](https://github.com/symfony/demo) application.
In `Dockerfile.symfony` we check out to the last commit at 2024-02-26, to ensure that the application is running on PHP 8.1.
We also install `composer` and `symfony` CLI tools, the PHP extensions required by the application, and then install the Composer dependencies.
Then, because we installed Docker, but did not create the alias, we need to run the Symfony command with the full path to the binary (`/root/.symfony5/bin/symfony`). We use the `serve` command to start the application.

### MySQL

We use the official MySQL image, and set the root password and the database name in the `docker-compose.yml` file.
We mount the container on the same network as the Symfony application, so that the Symfony application can access the database using the container name as the host (`db`).
