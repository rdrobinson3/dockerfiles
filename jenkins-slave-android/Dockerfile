FROM thedrhax/android-sdk:latest

MAINTAINER Dmitry Karikh <the.dr.hax@gmail.com>

USER root

# Install some useful but optional packages
RUN apt-get update \
 && apt-get install -y socat \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists /var/cache/apt

USER user

# Slave settings
ENV JENKINS_MASTER_USERNAME="jenkins" \
    JENKINS_MASTER_PASSWORD="jenkins" \
    JENKINS_MASTER_URL="http://jenkins:8080/" \
    JENKINS_SLAVE_MODE="exclusive" \
    JENKINS_SLAVE_NAME="swarm-$RANDOM" \
    JENKINS_SLAVE_ROOT="/home/user/jenkins-slave" \
    JENKINS_SLAVE_WORKERS="1" \
    JENKINS_SLAVE_LABELS=""

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
