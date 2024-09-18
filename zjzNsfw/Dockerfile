FROM node:16-alpine

WORKDIR /zjzNsfw

COPY  package.json yarn.lock ./
RUN --mount=type=cache,id=yarn-store,target=/root/.yarn-store \
    yarn install --frozen-lockfile

COPY . .
ARG NODE_ENV=""
RUN env ${NODE_ENV} yarn start

EXPOSE 3006
