# Demo Flutter "Hello World"

Demonstrate:

* Flutter Google UI toolkit

* Dart programming language

* Android Studio IDE

* Simple "Hello World" application


Contents:

* [Preflight](#preflight)
  * [Install Android Studio](#install-android-studio)
  * [Install Intel HAXM](#install-intel-haxm)
  * [Install Flutter](#install-flutter)
  * [Install plugins for Flutter and Dart](#install-plugins-for-flutter-and-dart)
* [Create Flutter "Hello World" application](#create-flutter-hello-world-application)
  * [Create the source code](#create-the-source-code)
  * [Choose the SDK](#choose-the-sdk)
  * [Update the SDK](#update-the-sdk)
  * [Create an Android Virtual Device (AVD)](#create-an-android-virtual-device-avd)


## Preflight


### Install Android Studio

Install Android Studio Integrated Development Environment (IDE):

```sh
brew cask install android-studio
```


### Install Intel HAXM

Install Intel Hardware Accelerated Execution Manager (HAXM) accelerator for Android Emulator:

```sh
brew cask install intel-haxm
```

Verify the kernel extensions load HAXM:

```sh
kextstat | grep com.intel.kext.intelhaxm 
```


### Install Flutter

There are various ways to install Flutter on macOS, such as via file download, or via homebrew, or via git clone, etc. 

We prefer to install Flutter this way:

* Install via git clone, because we prefer git over a Flutter website file download.

* Clone the entire repo, because it includes upcoming versions that we want for testing.

* Move it to the directory `/opt/flutter` because this is where we prefer software packages.


```sh
git clone https://github.com/flutter/flutter.git
sudo mv flutter /opt
export PATH="$PATH:/opt/flutter/bin"
```

Verify:

```sh
flutter doctor
```

Output such as:

```sh
Downloading Dart SDK...
Building flutter tool...
```

Accept licenses:

```sh
flutter doctor --android-licenses
```

Precache:

```sh
flutter precache
```


### Install plugins for Flutter and Dart

Launch Android Studio.

Choose "Plugins".

Install the plugin "Flutter" and the plugin "Dart".


## Create Flutter "Hello World" application


### Create the source code

Launch Android Studio.

Create a new Flutter app.

For this demo, we use these settings:

* Project name: `demo_flutter_hello_world`

* Flutter SDK path: `/opt/flutter`

* Project location: `~/git/joelparkerhenderson/`

* Description: Demonstrate Flutter "Hello World" application.

* Package name: com.joelparkerhenderson.demoflutterhelloworld

Android Studio should launch a typical source code editor.


### Choose the SDK

Use menu "File" -> "Project Structure" -> "Project Settings" -> "Project".

Select the SDK, which is set to [No SDK] by default.

We choose "Android API 29 Platform".

If there's nothing in the drop-down box, then select New, select Android SDK, navigate to your Android SDK location, then select the Android API <version> Platform.


### Update the SDK

Use menu "Tools" -> "SDK Manager".

This opens Settings -> Appearance & Behavior -> System Settings -> Android SDK.

Choose the tab "SDK Tools".

Click the "Edit" link next to the "Android SDK Location" box. This opens a new dialog for SDK Components Setup.

You should now see that "Android SDK - (installed)" has a tick in the checkbox, as do any SDK Platforms you have. 

Click on the button "Next" then your SDK will update.


### Create an Android Virtual Device (AVD)

An Android Virtual Device (AVD) is a configuration that defines the characteristics of an Android phone, tablet, Wear OS, Android TV, or Automotive OS device that you want to simulate in the Android Emulator. 

Use menu "Tools" -> "AVD Manager".

We prefer to create a phone virtual device, so we choose "Phone".

We prefer to create a "Pixel 3a" virtual device, because it's a decent typical phone.

We prefer to use the newest stable operating system, which at the time of writing is "Q".

Android Studio should now create the AVD Phone Pixel 3a with R operating system.


### Run the app

Use menu "Run" -> "Run".

You may see two options for "main.dart": one has a Dart icon, one has a Flutter icon. Choose the Flutter one.

Android Studio should show the bottom status bar work in progress, such as: Running Gradle task 'assembleDebug'. This may take a while (e.g. 10 minutes) because Android Studio may need to download more software.

Output:

```
Launching lib/main.dart on Android SDK built for x86 in debug mode...
Running Gradle task 'assembleDebug'...
✓ Built build/app/outputs/flutter-apk/app-debug.apk.
Installing build/app/outputs/flutter-apk/app.apk...
Waiting for Android SDK built for x86 to report its views...
Debug service listening on ws://127.0.0.1:52415/5w3MSveafuk=/ws
Syncing files to device Android SDK built for x86...
```

The emulator should launch the app, and should show the main page, titled "Flutter Demo Home Page".
