# Download/Install SDK

Install Intel HAXM and improve performance on desktop:

* <https://software.intel.com/en-us/android/articles/intel-hardware-accelerated-execution-manager/>

Download and install SDK tools:

* <http://developer.android.com/sdk/installing/index.html?pkg=tools>

Select the following along with default:

* Extra
  * Intel x86 Emulator Accelerator
  * Google Repository
  * Google Play services

You don't need the following packages (they are checked by default) if you only want to use the emulator:

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
  * Choose "Device Definition" tab -> "Nexus 5"
  * Click "Create AVD" and set the following
    * Target -> "Google APIs"
    * CPU -> "Atom x86_64"
    * Skin -> "Skin with dynamic hardware controls"
    * RAM -> use 2048 if your RAM is large enough
    * Front camera/Back camera
    * Check "Use host GPU"
  * Create the AVD
  * Choose "Android Virtual Devices" tab and start the emulator
    * Check "Scale display to real size"
    * Monitor dpi -> 118 (depends on screen size)
  * The initialization is slow, be patient.

See the following details:

* <http://developer.android.com/tools/help/emulator.html>
* <http://developer.android.com/tools/devices/emulator.html>
* <http://stackoverflow.com/questions/1554099/why-is-the-android-emulator-so-slow-how-can-we-speed-up-the-android-emulator>

# Install APK

* Find adb under C:\Users\<user name>\AppData\Local\Android\android-sdk\platform-tools
* type `adb install <path to apk>`
* If you see the following message, that means this APK was not built for this hardware architecture.
  * `Failure [INSTALL_FAILED_NO_MATCHING_ABIS]`

<http://developer.android.com/tools/help/adb.html>