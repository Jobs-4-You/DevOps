FROM node:lts-alpine3.11 AS builder
ARG envfile
WORKDIR  /src
COPY ./Webapp/package* ./
RUN npm ci --verbose
COPY ./Webapp/ .
COPY $envfile ./.env
RUN npm run build
RUN npm prune --production

FROM node:lts-alpine3.11
WORKDIR /app
COPY --from=builder /src/node_modules /app/node_modules
COPY --from=builder /src/package.json /app/package.json
COPY --from=builder /src/.next /app/.next
ENV NODE_ENV production
CMD npm run start