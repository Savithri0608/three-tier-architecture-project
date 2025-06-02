FROM mysql:8.0

VOLUME /data

ENV MYSQL_ALLOW_EMPTY_PASSWORD=yes \
    MYSQL_DATABASE=cities \
    MYSQL_USER=shipping \
    MYSQL_PASSWORD=secret

# Optional: Set default authentication plugin if needed for compatibility
ENV MYSQL_ROOT_PASSWORD=root
CMD ["--default-authentication-plugin=mysql_native_password"]

# Copy and run custom configuration script (ensure it has a shebang!)
COPY config.sh /root/
RUN chmod +x /root/config.sh && /root/config.sh

# Copy initialization SQL/scripts
COPY scripts/* /docker-entrypoint-initdb.d/
