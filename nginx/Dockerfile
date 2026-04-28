FROM nginx:1.27.5-alpine

RUN rm /etc/nginx/conf.d/default.conf 2>/dev/null || true

COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 80

STOPSIGNAL SIGTERM

CMD ["nginx", "-g", "daemon off;"]
