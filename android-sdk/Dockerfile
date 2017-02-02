FROM openjdk:8

MAINTAINER Dmitry Karikh <the.dr.hax@gmail.com>

# Install Git and dependencies
RUN dpkg --add-architecture i386 \
 && apt-get update \
 && apt-get install -y file git curl zip libncurses5:i386 libstdc++6:i386 zlib1g:i386 \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists /var/cache/apt

# Create a non-root user
RUN useradd -m user
USER user
WORKDIR /home/user

# Set up environment variables
ENV ANDROID_HOME="/home/user/android-sdk-linux" \
    SDK_URL="https://dl.google.com/android/repository/tools_r25.2.3-linux.zip" \
    GRADLE_URL="https://services.gradle.org/distributions/gradle-3.3-all.zip"

# Preserve temporary files between builds
#VOLUME /home/user/.gradle
#VOLUME /home/user/.android

# Install Android SDK
RUN mkdir -p $ANDROID_HOME \
 && cd $ANDROID_HOME \
 && curl -o sdk.zip $SDK_URL \
 && unzip sdk.zip \
 && rm sdk.zip

COPY ./licenses $ANDROID_HOME/licenses

# Install Gradle
RUN wget $GRADLE_URL -O gradle.zip \
 && unzip gradle.zip \
 && mv gradle-3.3 gradle \
 && rm gradle.zip

ENV PATH="/home/user/gradle/bin:${ANDROID_HOME}/tools:${ANDROID_HOME}/platform-tools:${PATH}"

