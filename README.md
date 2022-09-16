# Portfolio Server

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)

| Repository                                                          | Info               |
|---------------------------------------------------------------------|--------------------|
| [portfolio-client](https://github.com/FaZeRs/portfolio-client)      | Frontend           |
| [portfolio-api](https://github.com/FaZeRs/portfolio-api)            | Rest API           |
| [portfolio-server](https://github.com/FaZeRs/portfolio-server)      | Docker Environment |

## Features

- ⚡️[Traefik 2](https://github.com/traefik/traefik/) - The Cloud Native Application Proxy

- 💻 [MySQL](https://github.com/mysql/mysql-server) - Database

- 🍪 [Redis](https://github.com/redis/redis) - In-Memory database

- 📦 [Minio](https://github.com/minio/minio) - Multi-Cloud Object Storage

- 👀 [Watchtower](https://github.com/containrrr/watchtower) - Automating Docker container base image updates

## Installation

Create a `.env` file from the template `.env.template` file.
```bash
cp .env.template .env
```

Generate public and private key pair for jwt authentication:

### With docker

Run this command:
```bash
./scripts/generate-jwt-keys
```

It will output something like this. You only need to add it to your `.env` file.
```
To setup the JWT keys, please add the following values to your .env file:
API_JWT_PUBLIC_KEY_BASE64="(long base64 content)"
API_JWT_PRIVATE_KEY_BASE64="(long base64 content)"
```

### Without docker

```bash
$ ssh-keygen -t rsa -b 2048 -m PEM -f jwtRS256.key
# Don't add passphrase
$ openssl rsa -in jwtRS256.key -pubout -outform PEM -out jwtRS256.key.pub
```

You may save these key files in `./local` directory as it is ignored in git.

Encode keys to base64:

```bash
$ base64 -i local/jwtRS256.key

$ base64 -i local/jwtRS256.key.pub
```

Must enter the base64 of the key files in `.env`:

```bash
API_JWT_PUBLIC_KEY_BASE64=BASE64_OF_JWT_PUBLIC_KEY
API_JWT_PRIVATE_KEY_BASE64=BASE64_OF_JWT_PRIVATE_KEY
```

## Usage

```bash
$ docker compose up
```
