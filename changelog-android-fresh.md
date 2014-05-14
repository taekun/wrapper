# Changelog for AppGyver Scanner (Fresh Android)

## 0.4 (2014-05-14): Chromium on Android 4.x

* Remote debugging with Chrome works with Android 4.x devices (open `about:inspect` in Chrome).
* Steroids apps are more consistent between different devices because the browser engine doesn't depend on Android's version.
* You can use newest HTML5 features on all Android 4.x devices.
* On our Canvas rendering tests, Fresh Android is 2-3 times faster using Chromium than the Android 4.4 default WebView.
* Fresh Android with platform WebView supports API levels 10-19 (Android 2.3.3 - 4.4).
* Fresh Android Chromium supports API levels 14-19 (Android 4.x).
* Chromium will add 22 MB to the APK file size. Therefore Fresh Android Chromium is its own build target in the Build Service. The APK size using the platform WebView (without Chromium) is around 1 MB.

## 0.3 (2014-05-02): Remote Debugging on Android 4.4

* Remote debugging with Chrome on Android 4.4
	* Connect your 4.4 device with a cable and open `about:inspect` in Chrome.


## 0.2 (2014-04-28): Android 2.3 Support

* Android 2.3 support (API levels 10-19)
	* Minimum SDK level can be configured in Build Service.
	* Maximum SDK level setting has no effect for Fresh Android.
	* See [Android Developer guide](http://developer.android.com/guide/topics/manifest/uses-sdk-element.html) for details about selecting an SDK level.

## 0.1 (2014-04-15): Launch!

First beta release!

Supported Android versions:
Android 3.0.x (API level 11) to Android 4.4 (API level 19)

Supported features:

* Single-Page Applications from a File URL. File URLs start without a leading slash, eg. "index.html".
* Start application from a scanned QR code which points to Steroids CLI.
* Steroids CLI refresh will reload project.
* Buildable from AppGyver Build Service having adhoc, scanner and Google Play as build targets.
* Supported settings in Build Service:
	* Keystore
	* Prodution, Ad Hoc and Scanner Build settings EXCEPT min/max SDK level
	* Icons