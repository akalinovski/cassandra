# OpsCenter
#
# VERSION		1.0

FROM centos:centos7

# Add repo
ADD src/datastax.repo /etc/yum.repos.d/datastax.repo
ADD src/epel7.repo /etc/yum.repos.d/epel7.repo

# Install datastax OpsCenter and supervisor
RUN yum install -y openssh-clients opscenter which hostname supervisor

# Configure supervisord
ADD src/supervisord.conf /etc/supervisord.conf
RUN mkdir -p /var/log/supervisor

ADD src/start.sh /usr/local/bin/start

RUN chmod 777 /etc/supervisord.conf && \
    chmod 777 -R /var/log/supervisor && \
    chmod 777 /var/log && \
    chmod 777 -R /etc/opscenter && \
    chmod 777 -R /var/lib/opscenter && \
    chmod 777 -R /usr/share/opscenter/ && \
    chmod 777 -R /var/log/opscenter && \
    chmod 777 /usr/share/opscenter/bin/opscenter

# See http://www.datastax.com/documentation/opscenter/4.0/opsc/reference/opscPorts_r.html
EXPOSE 8888 61620 50031
USER root 
# CMD start 
CMD ["sh", "/usr/share/opscenter/bin/opscenter"]
