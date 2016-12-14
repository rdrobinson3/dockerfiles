FROM frekele/gradle:3.2.1-jdk8

MAINTAINER Dmitry Karikh <the.dr.hax@gmail.com>

# Install Git and dependencies
RUN dpkg --add-architecture i386 \
 && apt-get update \
 && apt-get install -y git libncurses5:i386 libstdc++6:i386 zlib1g:i386 \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists /var/cache/apt

# Install Android SDK
ENV ANDROID_HOME="/opt/android-sdk-linux" \
    PATH="${PATH}:${ANDROID_HOME}/tools:${ANDROID_HOME}/platform-tools" \
    SDK_URL="https://dl.google.com/android/repository/tools_r25.2.3-linux.zip"

RUN mkdir -p $ANDROID_HOME \
 && cd $ANDROID_HOME \
 && curl -o sdk.zip $SDK_URL \
 && unzip sdk.zip \
 && rm sdk.zip

RUN echo y | $ANDROID_HOME/tools/android update sdk --filter tools --no-ui --force -a \
 && echo y | $ANDROID_HOME/tools/android update sdk --filter platform-tools --no-ui --force -a \
 && echo y | $ANDROID_HOME/tools/android update sdk --filter build-tools-25.0.2 --no-ui --force -a \
 && echo y | $ANDROID_HOME/tools/android update sdk --filter android-25 --no-ui --force -a
