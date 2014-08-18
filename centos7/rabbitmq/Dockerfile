# https://github.com/tutumcloud/tutum-docker-rabbitmq
#
FROM centos:centos7
MAINTAINER ajchida@gmail.com

# Install RabbitMQ
RUN yum -y update
RUN yum -y install http://dl.fedoraproject.org/pub/epel/beta/7/x86_64/epel-release-7-0.2.noarch.rpm
RUN yum -y install erlang pwgen
RUN rpm --import http://www.rabbitmq.com/rabbitmq-signing-key-public.asc
RUN yum -y install http://www.rabbitmq.com/releases/rabbitmq-server/v3.3.4/rabbitmq-server-3.3.4-1.noarch.rpm
RUN rabbitmq-plugins enable rabbitmq_management

# Add scripts
ADD run.sh /run.sh
ADD set_rabbitmq_password.sh /set_rabbitmq_password.sh
RUN chmod 755 ./*.sh

EXPOSE 5672 15672
CMD ["/run.sh"]
