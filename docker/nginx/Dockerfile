FROM nginx:stable-alpine

COPY docker/nginx/nginx.conf /etc/nginx/nginx.conf
COPY dist /app

EXPOSE 80

ENTRYPOINT []

CMD ["nginx", "-g", "daemon off;"]
