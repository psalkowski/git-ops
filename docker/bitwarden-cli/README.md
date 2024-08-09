# bitwarden-cli

Build bitwarden-cli by calling:
```
docker buildx build --build-arg BW_CLI_VERSION=2024.7.2  -t namerci/bitwarden-cli:2024.7.2 --platform=linux/amd64,linux/arm64 . --push
```
