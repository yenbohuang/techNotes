# Download/Install SDK

Download and install SDK tools:

* <http://developer.android.com/sdk/installing/index.html?pkg=tools>

You don't need the following packages (they are checked by default) if you only want to use the emulator:

* Tools
  * Android SDK build tools
* Android <version>
  * Documentation for Android SDK
  * Samples for SDK
  * Android TV related packages
  * Sources for Android SDK

The following folders are created:

* C:\Users\<user name>\AppData\Local\Android
* C:\Users\<user name>\.android

# Start Emulator

* Start AVD Manager
  * Choose "Device Definition" tab -> "Galaxy Nexus"
  * Click "Create AVD" and set the following
    * CPU -> "ARM"
    * Skin -> HVGA
    * RAM -> 768 (use 2048 if your RAM is large enough)
    * Front camera/Back camera
    * Internal storage
    * SD card size
    * Use host GPU
  * Create the AVD
  * Choose "Android Virtual Devices" tab and start the emulator
  * The initialization is slow, be patient.

See the following details:

* <http://developer.android.com/tools/help/emulator.html>
* <http://developer.android.com/tools/devices/emulator.html>
* <http://developer.android.com/intl/zh-tw/tools/devices/emulator.html>

# Install APK

<http://developer.android.com/tools/help/adb.html>