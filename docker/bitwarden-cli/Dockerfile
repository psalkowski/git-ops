FROM node:18.18-alpine3.18 as builder

ARG BW_CLI_VERSION=2024.3.1
ENV HUSKY_SKIP_HOOKS=1

WORKDIR /app

RUN apk add --no-cache python3 make gcc g++ libc6-compat

RUN wget https://github.com/bitwarden/clients/archive/refs/tags/cli-v$BW_CLI_VERSION.tar.gz \
    && tar --strip-components=1 -xvf cli-v$BW_CLI_VERSION.tar.gz \
    && npm ci \
    && npm run dist:lin --workspace apps/cli

FROM alpine:3.18

RUN apk add --no-cache bash

COPY --from=builder /app/apps/cli/dist/linux/bw /usr/local/bin/bw
COPY entrypoint.sh /

RUN chmod +x /usr/local/bin/bw

ENTRYPOINT ["/entrypoint.sh"]
