FROM debian:11
MAINTAINER lgirardi <l@k8s.it>

EXPOSE 25/tcp

RUN apt-get -y update && DEBIAN_FRONTEND=noninteractive apt-get --no-install-recommends -y install \
	postfix \
	bsd-mailx \
	opendkim \
	opendkim-tools \
	sasl2-bin \
	rsyslog \
        supervisor


# Add files
ADD run.sh /opt/run.sh

# Run
CMD /opt/run.sh;/usr/bin/supervisord -c /etc/supervisor/supervisord.conf







