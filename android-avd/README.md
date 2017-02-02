This image contains the latest version of Android SDK with configured AVD.

# Example

* `docker run -it --privileged -p 5554:5554 -p 5555:5555 thedrhax/android-avd:latest bash`
* `adb connect 127.0.0.1`
* `adb devices` or `adb shell`

`--privileged` is required to access the /dev/kvm which is required to enable CPU hardware acceleration.
