FROM node:18.18-alpine3.18

ARG BW_CLI_VERSION

RUN apk add --no-cache python3 make gcc g++ libc6-compat bash
RUN npm install -g @bitwarden/cli@${BW_CLI_VERSION} \
    && npm cache clean --force

COPY entrypoint.sh /

ENTRYPOINT ["/entrypoint.sh"]
