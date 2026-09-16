# Ceksu Digital Badge

## Student

**Name:** Pattharaprapha Wongmuengklang

**Major:** Computer Engineering

**University:** Kalasin University

## Docker Hub

Image:

`pattharaprapha/ceksu-badge`

Tags:

* `1.0`
* `1.1`

## Run Version 1.0

```bash
docker pull pattharaprapha/ceksu-badge:1.0
docker run -d -p 8083:80 pattharaprapha/ceksu-badge:1.0
```

Open:

`http://localhost:8083`

## Docker Compose

Run:

```bash
docker compose up -d --build
```

Check:

```bash
docker compose ps
```

Open my badge:

`http://localhost:8083`

Open friend badge:

`http://localhost:8084`

Stop:

```bash
docker compose down
```

## Project Structure

```text
student-badge/
├── index.html
├── Dockerfile
├── .dockerignore
├── docker-compose.yml
├── REPORT.md
├── README.md
└── screenshots/
    ├── 01-local-run.png
    ├── 02-dockerhub-tags.png
    ├── 03-pull-proof.png
    ├── 04-inspect-friend.png
    └── 05-compose-two-tabs.png
```
