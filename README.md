# 🐳 WhaleWatcher
A smarter, more flexible Dokcer auto-updater with transparency and control


WhaleWatcher is a lightweight and opinionated alternative to Watchtower, built in Go. It monitors your running Docker containers and automatically updates them when new images are available.

Whether you're running a home server or managing a small fleet of containers, WhaleWatcher keeps your services up to date with minimal fuss.
🚀 Features

    ✅ Periodically checks for new versions of running container images

    🔄 Pulls and restarts containers with the latest image

    🧠 Smart restart logic to minimize downtime

    📜 Simple configuration via CLI flags or environment variables

    🐙 Optional integration with Docker Compose labels

    🛡️ Graceful shutdown and cleanup

🧰 Getting Started
Prerequisites

    Docker

    Go 1.20 or higher (for building from source)

🔧 Build from Source

git clone https://github.com/yourusername/whalewatcher.git
cd whalewatcher
go build -o whalewatcher ./cmd/whalewatcher

🐳 Run with Docker

docker run \
  -v /var/run/docker.sock:/var/run/docker.sock \
  yourusername/whalewatcher:latest

    Note: Mounting the Docker socket is required for WhaleWatcher to interact with the Docker API.

⚙️ CLI Options
Flag	Description	Default
--interval	Check interval (e.g. 30m, 1h)	5m
--cleanup	Remove old images after update	false
--watch-stopped	Watch stopped containers as well	false
--label-filter	Only watch containers with this label	""
--dry-run	Show actions without applying them	false
📦 Example: Docker Compose

services:
  whalewatcher:
    image: yourusername/whalewatcher:latest
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
    environment:
      - INTERVAL=15m
      - CLEANUP=true

