FROM node:16-alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm run build
COPY . .

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /user/share/nginx/html