This is modified version of https://github.com/phonegap/phonegap-app-developer, forked to https://github.com/terikon/phonegap-app-developer.
master branch should not be modified. Use branches for modifications.

# Changes from orininal phonegap-app-developer

This modified version supports access to DCIM folder, with [cordova-plugin-file](https://cordova.apache.org/docs/en/latest/reference/cordova-plugin-file/).

- cdvfile:// protocol is supported with config.xml, as described [here](https://cordova.apache.org/docs/en/latest/reference/cordova-plugin-file/#cdvfile-protocol).

- Permissions configuration with config.xml added with [cordova-custom-config](https://github.com/dpa99c/cordova-custom-config).

- Removed cordova-plugin-socialsharing as it breaks cordova-custom-config (waiting for fix, discussion is [here](https://github.com/dpa99c/cordova-custom-config/issues/51)).

- Removed com.wikitude.phonegap.WikitudePlugin as it just compiles too long.

- Added plugin https://github.com/subitolabs/cordova-gallery-api

# Android

To build:

    npm install
    npm run phonegap -- build android
    adb -e install ./platforms/android/build/outputs/apk/android-debug.apk # for emulator
    adb -d install ./platforms/android/build/outputs/apk/android-debug.apk # for device    

For this to work, add permission for storage in **settings/apps/phonegap**. 

# iOS

Be careful! Build cleans the platforms folder, so all changes in plugins will be removed.
To build:

    npm install
    npm run phonegap -- run ios
    # or
    npm run phonegap -- build ios
    
Install [ios-deploy](https://github.com/phonegap/ios-deploy) if needed.
