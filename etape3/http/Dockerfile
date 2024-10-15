FROM nginx:latest

COPY config/nginx.conf /etc/nginx/conf.d/default.conf
COPY src/ /app

EXPOSE 8080

CMD ["nginx", "-g", "daemon off;"]