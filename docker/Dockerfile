FROM node:18-alpine AS builder
WORKDIR /app
COPY ./app/package*.json ./
RUN  npm install
COPY ./app/. .
RUN npm run build



FROM node:18-alpine AS final

WORKDIR /app
ADD ./app/package.json .
COPY --from=builder /app/.output ./
COPY --from=builder /app/node_modules ./node_modules

ENV HOST=0.0.0.0
ENV PORT=80
EXPOSE 80

VOLUME ./volumes/config
VOLUME ./volumes/data

CMD ["node", "./server/index.mjs"]