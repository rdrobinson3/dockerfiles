This image expands [frekele/gradle](https://hub.docker.com/r/frekele/gradle/) with latest Android SDK.

# Example

* `docker run -it thedrhax/android-sdk:25 bash`

# Problems and solutions

## Gradle doesn't detect the SDK

Add this line to `local.properties`: `sdk.dir=/opt/android-sdk-linux`

## Persistent cache

Add this parameter to `docker run` command: `-v /your/path/here:/root/.gradle`
