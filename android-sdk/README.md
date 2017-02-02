This image contains the latest versions of Android SDK and Gradle.

# Example

* `docker run -it thedrhax/android-sdk:last bash`

# Problems and solutions

## Gradle doesn't detect the SDK

Add this line to `local.properties`: `sdk.dir=/opt/android-sdk-linux`

## Persistent cache

Add this parameter to `docker run` command: `-v /your/path/here:/home/user/.gradle`
