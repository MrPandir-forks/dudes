<h1 align="center">Dudes</h1>
<div align="center">
  <a
  href="https://vscode.dev/redirect?url=vscode://ms-vscode-remote.remote-containers/cloneInVolume?url=https://github.com/inferst/dudes">
    <img
    src="https://img.shields.io/static/v1?style=for-the-badge&logo=docker&label=devcontainer&message=supported&color=0797ff&labelColor=000000"
    alt="Dev Containers Badge"
    />
  </a>
</div>

<img
src="https://static-cdn.jtvnw.net/emoticons/v2/emotesv2_83ffd63c128c4fbc86784ff2914836a9/default/dark/4.0"
width="100px"
align="right"
/>

Animated characters for chatters in your stream.

# Develop in devcontainer

> [!IMPORTANT]
> You need the [docker](https://docs.docker.com/get-docker/) installed and running.

Just install the [extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) and build it lol.

In the development container, you'll have access to `docker` and a convenient alias `dudes`. This alias executes `docker compose -p dudes -f compose.dev.yaml`, streamlining your workflow.

For example, to view the logs in real time:
```shell
dudes logs -f
```

# Run via docker compose

1. Copy environment variables
    ```shell
    cp .env.example .env
    ```
2. Run docker compose
    ```shell
    docker compose -f compose.dev.yaml up -d
    ```

## Run only the database

If you only need to run the database:
```shell
docker compose -f compose.dev.yaml run -d postgres
```

> [!WARNING]
> By default, PostgreSQL runs on port `5432`. Before starting, ensure this port is not already in use on your system.

To change the PostgreSQL port, use the following command structure:
```shell
docker compose -f compose.dev.yaml run -d -p <port>:5432 postgres
```

# Run locally

> [!IMPORTANT]
> You need [node](https://nodejs.org/en/download/package-manager) installed.

1. Copy environment variables
    ```shell
    cp .env.example .env
    ```
2. Install and run postgres

    You can install [PostgreSQL](https://www.postgresql.org/download/) directly on your system or use Docker. For Docker instructions, refer to [Run only the Database](<#run-only-the-database>).
3. Install pnpm
    ```shell
    npm install -g pnpm
    ```
4. Install dependencies 
    ```shell
    pnpm install
    ```
5. Generate schema and migrate
    ```shell
    pnpm run db:migrate:dev
    ```
6. Start the server
    ```shell
    pnpm run dev
    ```

# Ports

- http://localhost:3000 - admin panel backend
- http://localhost:4200 - admin panel frontend
- http://localhost:4300 - client

# Run the linter

```shell
pnpm run lint
```
