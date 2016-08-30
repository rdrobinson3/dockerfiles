FROM java:openjdk-8-jdk-alpine

MAINTAINER Dmitry Karikh <the.dr.hax@gmail.com>

# Slave settings
ENV JENKINS_MASTER_USERNAME="jenkins" \
    JENKINS_MASTER_PASSWORD="jenkins" \
    JENKINS_MASTER_URL="http://jenkins:8080/" \
    JENKINS_SLAVE_MODE="exclusive" \
    JENKINS_SLAVE_NAME="swarm-$RANDOM" \
    JENKINS_SLAVE_ROOT="/opt/jenkins-slave" \
    JENKINS_SLAVE_WORKERS="1" \
    JENKINS_SLAVE_LABELS=""

# Install curl
RUN apk --no-cache add curl

# Install Jenkins slave (swarm)
ADD swarm.jar /

ENTRYPOINT java -jar /swarm.jar \
                -disableClientsUniqueId \
                -username $JENKINS_MASTER_USERNAME \
                -password $JENKINS_MASTER_PASSWORD \
                -mode $JENKINS_SLAVE_MODE \
                -name $JENKINS_SLAVE_NAME \
                -executors $JENKINS_SLAVE_WORKERS \
                -master $JENKINS_MASTER_URL \
                -fsroot $JENKINS_SLAVE_ROOT \
                -labels "$JENKINS_SLAVE_LABELS swarm"
