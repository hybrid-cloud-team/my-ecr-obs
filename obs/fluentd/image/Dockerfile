# ===============================
# Fluentd (Production Base)
# ===============================
FROM fluent/fluentd:v1.16-1

USER root

WORKDIR /fluentd

RUN apk add --no-cache \
    build-base \
    ruby-dev \
    curl \
    tzdata \
 && rm -rf /var/cache/apk/*

RUN gem install \
    fluent-plugin-elasticsearch:5.3.0 \
    fluent-plugin-kubernetes_metadata_filter:3.2.0 \
    fluent-plugin-record-reformer:1.3.0 \
    fluent-plugin-prometheus:2.0.2 \
    fluent-plugin-s3:1.7.0 \
    --no-document

ENV TZ=Asia/Seoul

RUN chown -R fluent:fluent /fluentd

USER fluent

CMD ["fluentd", "-c", "/fluentd/etc/fluent.conf", "-p", "/fluentd/plugins"]
