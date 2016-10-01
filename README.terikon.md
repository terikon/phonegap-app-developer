This is modified version of https://github.com/phonegap/phonegap-app-developer, forked to https://github.com/terikon/phonegap-app-developer.
master branch should not be modified. Use branches for modifications.

# Modify plugins

**Be careful!** Running npm run build will remove platforms folder, and all changes to plugins will be lost! Backup platforms folder frequently.

## For Android

TODO

## For iOS

- Open XCode project.
- Modify swift code in Plugins folder.
- Modify js code in Staging/www/plugins/ folder

# Changes from orininal phonegap-app-developer

This modified version supports access to DCIM folder, with [cordova-plugin-file](https://cordova.apache.org/docs/en/latest/reference/cordova-plugin-file/).

- cdvfile:// protocol is supported with config.xml, as described [here](https://cordova.apache.org/docs/en/latest/reference/cordova-plugin-file/#cdvfile-protocol).
- Permissions configuration with config.xml added with [cordova-custom-config](https://github.com/dpa99c/cordova-custom-config).
- Removed cordova-plugin-socialsharing as it breaks cordova-custom-config (waiting for fix, discussion is [here](https://github.com/dpa99c/cordova-custom-config/issues/51)).
- Removed com.wikitude.phonegap.WikitudePlugin as it just compiles too long.
- Added plugin https://github.com/terikon/cordova-plugin-photo-library
- Added plugin cordova-plugin-crosswalk-webview, v19 (v20 does not support Android 4.0)
- Removed barcode-scanner, and incorrect version used (use https://github.com/phonegap/phonegap-plugin-barcodescanner if needed, to prevent issues with xwalk).
- Added cordova-plugin-googleplus plugin
- Renamed app name to com.terikon.phonegap.app from com.adobe.phonegap.app
- Added cordova-plugin-safariviewcontroller

# Android

To build:

    npm install
    npm run phonegap -- build android
    adb -e install ./platforms/android/build/outputs/apk/android-x86-debug.apk # for emulator
    adb -d install ./platforms/android/build/outputs/apk/android-armv7-debug.apk # for device    

For this to work, add permission for storage in **settings/apps/phonegap**. 

# iOS

Be careful! Build cleans the platforms folder, so all changes in plugins will be removed.
To build:

    npm install
    npm run phonegap -- run ios
    # or
    npm run phonegap -- build ios
    
Install [ios-deploy](https://github.com/phonegap/ios-deploy) if needed.

To debug swift, open XCode project, and then change project > build settings > swift compiler-code generation > optimization level > debug > none
