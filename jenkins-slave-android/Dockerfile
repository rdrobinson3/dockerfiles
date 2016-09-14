FROM thedrhax/jenkins-slave-base:latest

MAINTAINER Dmitry Karikh <the.dr.hax@gmail.com>

# Install Ant, Git, etc.
RUN dpkg --add-architecture i386 \
 && apt-get update \
 && apt-get install -y ant git libncurses5:i386 libstdc++6:i386 zlib1g:i386 \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists /var/cache/apt

# Install Android SDK
ENV ANDROID_HOME="/opt/android-sdk-linux" \
    PATH="${PATH}:${ANDROID_HOME}/tools:${ANDROID_HOME}/platform-tools"

RUN cd $ANDROID_HOME/.. \
 && curl -o sdk.tgz https://dl.google.com/android/android-sdk_r24.4.1-linux.tgz \
 && tar -xzvf sdk.tgz && rm sdk.tgz

RUN echo y | $ANDROID_HOME/tools/android update sdk --filter tools --no-ui --force -a \
 && echo y | $ANDROID_HOME/tools/android update sdk --filter platform-tools --no-ui --force -a \
 && echo y | $ANDROID_HOME/tools/android update sdk --filter build-tools-24.0.2 --no-ui --force -a \
 && echo y | $ANDROID_HOME/tools/android update sdk --filter android-24 --no-ui --force -a
