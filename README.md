![Github Workflows](https://github.com/DeltaNedas/ExampleJavaMod/workflows/Java%20CI/badge.svg)

# ExampleJavaMod

A prototype Java Mindustry mod that works on Android and PC.
Uses a small makefile rather than gradle.

Download a precompiled build [here](https://github.com/DeltaNedas/ExampleJavaMod/releases/latest)

## Building for Desktop Testing

1. Install JDK 14 and curl. If you don't know how, look it up. If you already have any version of the JDK >= 8, that works as well.
On Debian unstable, `# apt install openjdk-14-jdk-headless curl`
2. Run `$ make install`
3. Test the desktop-only version that has been installed.
To build an Android-compatible version, you need the Android SDK. You can either let Github Actions handle this, or set it up yourself. See steps below.

# Building on Android

## With Github Actions

This repository is set up with Github Actions CI to automatically build the mod for you every commit. This requires a Github repository, for obvious reasons.
To get a jar file that works for every platform, do the following:
1. Make a Github repository with your mod name, and upload the contents of this repo to it. Perform any modifications necessary, then commit and push. 
2. Check the "Actions" tab on your repository page. Select the most recent commit in the list. If it completed successfully, there should be a download link under the "Artifacts" section. 
3. Click the download with no suffix. This will download a **zipped jar** - **not** the jar file itself [1]! Unzip this file and import the jar contained within in Mindustry. This version should work both on Android and Desktop. If you want to cut disk usage select the jar for your platform.

## Android SDK

This approach is more painful

1. Download the Android SDK, unzip it and set the `ANDROID_HOME` environment variable to its location.
2. Make sure you have API level 30 installed, as well as any recent version of build tools (e.g. 30.0.1)
3. Add a build-tools folder to your PATH. For example, if you have `30.0.1` installed, that would be `$ANDROID_HOME/build-tools/30.0.1`.
4. Run `$ make`. If you did everything correctly, this will create a jar file that can be run on both Android and desktop. 

--- 

*[1]: Yes, I know this is stupid. It's a Github UI limitation - while the jar itself is uploaded unzipped, there is currently no way to download it as a single file.*
