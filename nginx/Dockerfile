FROM debian:stretch-slim
MAINTAINER NGINX Docker Maintainers "docker-maint@nginx.com"

RUN useradd -d /nonexistent -s /bin/false -rM -c "nginx user,,,"  nginx

RUN apt-get update \
        && apt-get install --no-install-recommends --no-install-suggests -y \
                                                ca-certificates \
                                                nginx-extras \
                                                gettext-base \
        && rm -rf /var/lib/apt/lists/*

# forward request and error logs to docker log collector
RUN ln -sf /dev/stdout /var/log/nginx/access.log \
        && ln -sf /dev/stderr /var/log/nginx/error.log
        
COPY config /etc/nginx/

EXPOSE 80 443



CMD ["nginx", "-g", "daemon off;"]
