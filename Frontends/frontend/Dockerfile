# Build stage
FROM nginx:latest AS build-env
RUN rm -rf /usr/share/nginx/html/index.html
COPY code /usr/share/nginx/html/index.html
COPY nginx.conf /etc/nginx/nginx.conf

# Runtime stage (Distroless)
FROM gcr.io/distroless/base
COPY --from=build-env code /usr/share/nginx/html
COPY --from=build-env /etc/nginx/nginx.conf /etc/nginx/nginx.conf

CMD ["/usr/sbin/nginx", "-g", "daemon off;"]
