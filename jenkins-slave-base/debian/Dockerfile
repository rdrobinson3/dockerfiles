FROM java:8

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

# Install Jenkins slave (swarm)
ENV SWARM_CLIENT_URL="http://maven.jenkins-ci.org/content/repositories/releases"\
"/org/jenkins-ci/plugins/swarm-client/2.0/swarm-client-2.0-jar-with-dependencies.jar"

RUN mkdir -p $JENKINS_SLAVE_ROOT \
 && curl -Lo $JENKINS_SLAVE_ROOT/swarm.jar $SWARM_CLIENT_URL

ENTRYPOINT java -jar $JENKINS_SLAVE_ROOT/swarm.jar \
                -disableClientsUniqueId \
                -username $JENKINS_MASTER_USERNAME \
                -password $JENKINS_MASTER_PASSWORD \
                -mode $JENKINS_SLAVE_MODE \
                -name $JENKINS_SLAVE_NAME \
                -executors $JENKINS_SLAVE_WORKERS \
                -master $JENKINS_MASTER_URL \
                -fsroot $JENKINS_SLAVE_ROOT \
                -labels "$JENKINS_SLAVE_LABELS swarm"
