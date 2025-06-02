FROM fluentd

USER root

RUN apk update && \
    apk add --no-cache --virtual .build-dependencies build-base ruby-dev && \
    fluent-gem install fluent-plugin-elasticsearch && \
    fluent-gem install fluent-plugin-kubernetes_metadata_filter && \
    fluent-gem install fluent-plugin-multi-format-parser && \
    apk del .build-dependencies && \
    rm -rf /var/cache/apk/*

# Switch back to fluent user if applicable
USER fluent
