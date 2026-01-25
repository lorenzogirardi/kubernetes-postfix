FROM debian:12-slim
LABEL maintainer="lgirardi <l@k8s.it>"
LABEL version="0.4"
LABEL description="Postfix mail server with OpenDKIM for Kubernetes"

EXPOSE 25/tcp

RUN apt-get -y update && \
    DEBIAN_FRONTEND=noninteractive apt-get --no-install-recommends -y install \
    postfix \
    bsd-mailx \
    opendkim \
    opendkim-tools \
    sasl2-bin \
    rsyslog \
    supervisor \
    ca-certificates && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Add files
COPY run.sh /opt/run.sh
RUN chmod +x /opt/run.sh

# Run
CMD ["/bin/bash", "-c", "/opt/run.sh && /usr/bin/supervisord -c /etc/supervisor/supervisord.conf"]
