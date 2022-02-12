FROM node:16-alpine as builder

WORKDIR '/app'

COPY package.json .
RUN npm install

COPY . .

RUN npm run build

# RUN chown -R node /app

# USER node

FROM nginx

COPY --from=builder /app/build /usr/share/nginx/html
