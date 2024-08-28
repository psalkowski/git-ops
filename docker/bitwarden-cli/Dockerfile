FROM node:22-alpine3.19

ARG BW_CLI_VERSION

WORKDIR /app

RUN apk add --no-cache python3 make gcc g++ libc6-compat bash git

RUN npm install -g @bitwarden/cli@${BW_CLI_VERSION} \
    && npm cache clean --force

COPY entrypoint.sh /

ENTRYPOINT ["/entrypoint.sh"]
