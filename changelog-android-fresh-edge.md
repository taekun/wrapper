## 4.2.2-edge1 (2015-12-21):

- Fix issue where opening an InAppBrowser in Crosswalk build caused the app to crash. Will close [#1082](https://github.com/AppGyver/steroids/issues/1082)

## 4.0.7-edge1 (2015-06-21):

Features:
- Native loading spinner. Used in place of `loading.html` if the `loading-view` native style is set. See examples of the native CSS at the [Steroids.js next branch](https://github.com/AppGyver/steroids-js/blob/next/testApp/www/native-styles/android.css#L8-L16).
- Android CORS support with the `network.extraResponseHeaders` config in `config/app.coffee`. The following platform/OS limitations apply:
  -  **All Crosswalk builds:** the `extraResponseHeaders` config in general is not supported. However, the `"Access-Control-Allow-Origin"` key is parsed for allowed addresses as a comma-separated list, so e.g. `"Access-Control-Allow-Origin": "http://stackoverflow.com/*, http://google.com/*"` will allow cross-domain traffic from both Google and StackOverflow.
 - **Platform WebView builds on Android 5.0 and above:** the `extraResponseHeaders` config is fully supported.
 - **Platform WebView builds below Android 5.0:** no support for the `extraResponseHeaders` config.

## 4.0.6-rc1 (2015-06-17):

Features:
- `steroids.drawers.enable/disable`, requires Supersonic 1.5.8 or Steroids.js 3.5.12 (available in next branch on GitHub).
- Support for selecting a file on device with `<input type="file">`, closes [#426](https://github.com/AppGyver/steroids/issues/426).

## 4.0.6-edge4 (2015-06-12):

Changes:
- Wrapper loads application in a separate thread

Features:
- `steroids.view.navigationBar.setStyleCSS`, closes [#586](https://github.com/AppGyver/steroids/issues/586).

## 4.0.6-edge3 (2015-06-04):

Changes:
- Updated Pixate to latest version, with some minor bugfixes.
- Cordova `deviceready` event now prints a warning log line after 10 seconds instead of 5. This is to prevent false alarms when multiple preloads cause the event to fire late.

Bugfixes:
- Fixed native bridge related crash introduced in 4.0.6-edge2. Will close [#964](https://github.com/AppGyver/steroids/issues/964).
- Scanner no longer fails if one of the IPs included in QR code errors out before one of them invokes the success callback. Will close [#552](https://github.com/AppGyver/steroids/issues/552).
- Tab bar images now respond properly to taps again. Will close [#956](https://github.com/AppGyver/steroids/issues/956).
- Animation APIs no longer crash if given a duration that is not a number. Furthermore, string type durations are cast into numbers before evaluating them (i.e. `duration: "0.6"` works now). This is to match iOS behavior.

## 4.0.6-edge2 (2015-05-28):

Bugfixes:
- Tab bar icons can now be properly resized with native CSS on Android. Will close [#867](https://github.com/AppGyver/steroids/issues/867).
- Changed Android native bridge mode to `PRIVATE_API` to (hopefully) fix issues where Cordova callbacks would not fire (resulting also in `deviceready` not firing). Related issues [#722](https://github.com/AppGyver/steroids/issues/772), [#783](https://github.com/AppGyver/steroids/issues/783) and [#872](https://github.com/AppGyver/steroids/issues/872).

## 4.0.6-edge1 (2015-05-26):

Bugfixes:
- SVG icons now show up correctly in ad hoc builds. Will close [#632](https://github.com/AppGyver/steroids/issues/632).
- Navigation bar title is no longer misaligned when buttons are set on only one side. Will close [#843](https://github.com/AppGyver/steroids/issues/843).
- Can now push and replace layers from inside a drawer. Will close [#946](https://github.com/AppGyver/steroids/issues/946).
- Android Crosswalk apps no longer constantly consume 20% CPU. Will close [#583](https://github.com/AppGyver/steroids/issues/583) and [#841](https://github.com/AppGyver/steroids/issues/841).
- Cordova plugins that utilize the InAppBrowser plugin internally no longer create platform WebViews in Crosswalk builds. Will close [#933](https://github.com/AppGyver/steroids/issues/933).

## 4.0.5-edge12 (2015-04-01):

- Fix issue where Cordova `deviceready` event would not fire on Crosswalk builds harder. Will close [#722](https://github.com/AppGyver/steroids/issues/772).

## 4.0.5-edge11 (2015-03-18):

Breaking changes:
- The Android permissions `ACCESS_FINE_LOCATION`, `MODIFY_AUDIO_SETTINGS`, `RECORD_AUDIO` and `WAKE_LOCK` are no longer required automatically for all Android Crosswalk builds. Instead, you must set the applicable permissions in your app's Android Build Configuration page in the Build Service.

## 4.0.5-edge10 (2015-03-18):

Breaking changes:
- Deprecate `steroids.app.getLaunchURL()`.

Features:
- Add support for `steroids.app.getLaunchURI()`, which correctly returns the custom URI scheme used to launch the app. Will close [#868](https://github.com/AppGyver/steroids/issues/868).

## 4.0.5-rc1 (2015-03-18): Multiple Scanner applications

Features:
- Scanner supports multiple applications. You can scan the applications deployed
  to the cloud and keep them available for later use. Local Steroids CLI
  applications are displayed as one application, however.

## 4.0.5-edge9 (2015-03-12):

Changes:
- Update Facebook SDK to 3.21.1

## 4.0.5-edge8 (2015-03-11):

Bugfixes:
- Fixed an issue where opening an app via a custom URL scheme would not function correctly. Will close [#861](https://github.com/AppGyver/steroids/issues/861).

## 4.0.5-edge7 (2015-03-09):

Bugfixes:
- Fix issue where Cordova `deviceready` event would not fire on Crosswalk builds when numerous assets (i.e. JavaScript/CSS/image files) were loaded. Fixes [#722](https://github.com/AppGyver/steroids/issues/772).
- Fix issue where pages on Crosswalk would sometimes show blank before reload. Fixes [#771](https://github.com/AppGyver/steroids/issues/771).
- Fix issue where the `inAppBrowser` plugin would not perform POST and GET requests reliably in the background on Crosswalk builds. Fixes [#657](https://github.com/AppGyver/steroids/issues/657).

## 4.0.5-edge6 (2015-02-20):

Changes:
- Support for the fixed Push Notifications plugin (1.2.0). You can try it
  by including `https://github.com/AppGyver/PushNotifications.git#next`
  in the Build Service (please notice `#next` in the url).


## 4.0.5-edge5 (2015-02-11):

Bugfixes:
- Push with custom animation threw null pointer exception in some cases. Introduced in #482.
- A previously hidden tab bar was being displayed when calling `layer.push()`.

## 4.0.5-edge4 (2015-02-02): Custom Animations for layers.push

Features:
- Custom animations for layers.push. Delivers [#482](https://github.com/AppGyver/steroids/issues/482).

Bugfixes:
- Empty navigation bar was displayed when none was defined. Fixes [#729](https://github.com/AppGyver/steroids/issues/729).
- Update FileTransfer plugin to include cookie support for Crosswalk runtimes. It accidentally went missing after last plugin update.


## 4.0.5-edge3 (2015-01-29): Cordova plugin updates

Changes:
- Fix FileTransfer plugin errors; use 0.4.8 instead of the bleeding edge.
  Fixes [#791](https://github.com/AppGyver/steroids/issues/791).
- Update Camera plugin to 0.3.4

## 4.0.5-edge2 (2015-01-27): Update selected Cordova plugins

Changes:
- Update Cordova plugins:
  - FileTransfer: 0.4.9-dev
  - File: 1.3.2
  - Media: 0.2.16-dev
  - Media-Capture: 0.3.6-dev
  - InAppBrowser: 0.5.4

## 4.0.5-edge1 (2015-01-21):

Changes:
- Vertical scrolling in a drawer is now more sensitive and friendlier.
  See the test application for reference [how to adjust the values](https://github.com/AppGyver/steroids-js/pull/140/files).

## 4.0.4-edge6 (2015-01-20): Promoted to 4.0.4

Changes:
- Allow third party cookies on Android >= 5.0 when using the platform webview
  (delivers [#697](https://github.com/AppGyver/steroids/issues/697)).

## 4.0.4-edge5 (2015-01-19):

Bugfix:
- Ignore hiding of splash screen when application is shutting down.
  Fixes [#731](https://github.com/AppGyver/steroids/issues/731) harder.

## 4.0.4-edge4 (2015-01-16):

Bugfix:
- Sometimes application crashed when exiting with back button.
  Fixes [#731](https://github.com/AppGyver/steroids/issues/731).

## 4.0.4-edge3 (2014-12-23):

Features:
- Options for modal show and hide (animations, navigation bar)
- `steroids.screen.rotate` now fires callbacks for transition started and ended
- Support for [Push Notifications](https://github.com/AppGyver/PushNotifications)
plugin. Please see the [guide for setup instructions](http://docs.appgyver.com/supersonic/guides/).

Bugfixes:
- Fixed an issue where e.g. `ng-cordova.js` would be read from `ng-cordova-merged.js`
- Fixed an issue that emerged in 4.0.4-edge2 which broke `initialView.show`
- Modals were not discarded after hide or hideAll if they were non-preloaded. Fixes [#686](https://github.com/AppGyver/steroids/issues/686).

## 4.0.4-edge2 (2014-12-11):

Bugfixes:
- View thought it was hidden (`document.visibilityState && document.hidden`) when it was not if `visibilityChange` had not fired yet.
- `steroids.navigationBar` behaviour was inconsistent between Android and iOS in preloaded views. Fixes [#646](https://github.com/AppGyver/steroids/issues/646).
- `steroids.app.getMode` returned "scanner" in Standalone builds.
- Cordova plugins could not add native views because `CordovaWebViewInterface#getParent()` returned null. Fixes [#588](https://github.com/AppGyver/steroids/issues/588).
- `steroids.app.getLaunchURL` returned undefined even after launching from web.
- Fixed an issue that was causing a NPE when using the localStorage.
- The Cordova `backbutton` event fired incorrectly on the first page, e.g. not doing anything on the first press of the back button. Fixes [#617](https://github.com/AppGyver/steroids/issues/617).

## 4.0.4-edge1 (2014-12-09):

Bugfixes:
- Images in navigation bar title/buttons did not show up in Ad Hoc builds. Fixes [#651](https://github.com/AppGyver/steroids/issues/651).
- Unload gave a false success callback and did not unload the view. Fixes [#656](https://github.com/AppGyver/steroids/issues/656).
- The `visibilityState` for a preloaded view was incorrect. Fixes [#655](https://github.com/AppGyver/steroids/issues/655).
- Fixed splash screen `autohide: false`.
- Fixed a bug where after hiding a modal on top of a layer with back button in nav bar the back-indicator used to disappear.

## 4.0.3-edge2 (2014-12-02):

Changes:
- Speed up Cordova `deviceready` on all Android devices by changing the way Cordova's plugins are loaded. `deviceready` should now be ~1 second faster in 4.0.3-edge2 than in 4.0.2.

## 4.0.3-edge1 (2014-11-26):

Bugfixes:
- Fixed a bug where layer would stay hidden if `layers.pop` was called too soon after `layers.push`

## 4.0.2-edge7 (2014-11-25):

Bugfixes:
- If modal was open during rotation, it flashed the WebView below it quickly. Fixes [#609](https://github.com/AppGyver/steroids/issues/609).
- On Platform WebView contents of other tabs would sometimes flicker on screen.

## 4.0.2-edge6 (2014-11-24):

Changes:
- InitialView and Loading.html fade-in and fade-out transitions have been improved.

Bugfixes:
- Pause event would not fire when application goes to background, instead it fired when app resumed. Fixes [#634](https://github.com/AppGyver/steroids/issues/634)
- `steroids.navigationBar.update` used to erase buttons if they were not defined in the API call
- Fixed a rare crash that sometimes happened on app startup

## 4.0.2-edge5 (2014-11-21):

Changes:
- `getApplicationState()` now also returns `startURL` property, ie. the first url used in the WebView.

Bugfixes:
- Replacing layers from drawer made the center WebView forget Tab Bar (fixes [#608](https://github.com/AppGyver/steroids/issues/608)).


## 4.0.2-edge4 (2014-11-20):

Bugfixes:
- Fix crash which occurred when trying to evaluate Javascript on a killed WebView.


## 4.0.2-edge3 (2014-11-20):

(This edge was pulled back from the Build Service due to a severe regression in
one of these bugfixes.)

Bugfixes:
- `visibilitychange` was fired twice when modal is opened.
- App with tabs or drawer calling `broadcastJavascript`
  while having focus on input field caused unfocus, ie. keyboard disappeared
  (fixes [#626](https://github.com/AppGyver/steroids/issues/626))
- User Files take precedence over Steroids and Cordova assets when
  retrieving from http://localhost
  (fixes [#597](https://github.com/AppGyver/steroids/issues/597))
- Requesting an inexistent file gave an empty Javascript alert dialog
  on Crosswalk
  (fixes [#524](https://github.com/AppGyver/steroids/issues/524))
- Cordova FileTransfer plugin crashed with Cookies when using Crosswalk
  (fixes [#627](https://github.com/AppGyver/steroids/issues/627))


## 4.0.2-edge2 (2014-11-19):

Bugfixes:
- `visibilitychange` event was not fired on `hidden` event correctly. Fixes [#607](https://github.com/AppGyver/steroids/issues/607). Needs Steroids.js 3.5.8 or newer.

## 4.0.2-edge1 (2014-11-18):

Bugfixes:
- Eventlistener on a preloaded webview die after the preloaded view is popped
  (fixes [#619](https://github.com/AppGyver/steroids/issues/619))
- Device back button didn't work after `modal.hide()`
  (fixes [#610](https://github.com/AppGyver/steroids/issues/610))
- Tab Bar icons appeared as stretched on landscape or big screen devices
  (icon size must still be defined in `android.css`)

Changes:
- Compile with Android SDK 21


## 4.0.0 - 4.0.1

See changelog for stable releases.


## 4.0.0-rc1 (2014-11-08): Massive iOS Feature Parity

Features:
- Unload a WebView with `view.unload`.
- Crosswalk x86 builds:
  - Choose ARM, x86 or ARM+x86 support for Crosswalk builds.

Changes:
- Speed up layer transitions to be consistent with iOS (0.6s --> 0.3s).
- Upgrade build-tools to 21.1 and Android SDK to 21 (Android 5.0 Lollipop).
- Improve Pixate consistency between iOS and Android.

Bugfixes:
- Lock touch events and API calls during in-place animations
  (fixes [#539](https://github.com/AppGyver/steroids/issues/539)).
- Navigation Bar did not show title image.
- WebView load event caused an exception in Steroids.js.
- Back button events did not work on Crosswalk
  (fixes [#519](https://github.com/AppGyver/steroids/issues/519)).


## 4.0.0-edge3 (2014-11-05): Fix a Crosswalk crash

Bugfixes:
- Fix a nasty crash on Crosswalk runtimes.

## 4.0.0-edge2 (2014-11-05): Tab Bar API and View Events

Features:
- Update to Crosswalk 9 with Chromium 38.
- Native Chromium library is temporarily provided for both ARM and Intel x86.
  - This increases the minimum APK filesize of the Crosswalk builds to 34 MB.
    We will soon provide an option to build only for ARM or x86 in the Build Service.
- Implement view related events:
  - `visibilitychange` (requires Steroids.js 3.5.6)
  - `steroids.layers.on/off`
  - `steroids.modal.on/off`
  - `steroids.tabBar.on/off`
- Implement rest of Tab Bar API
  - `steroids.tabBar.replace`
  - `steroids.tabBar.currentTab.update`
- Extended drawer support
  - enable/disable gestures
  - change the drawer size
  - display shadow between the center view and drawer
- Drawer API methods
  - `steroids.drawers.update`
  - `steroids.drawers.show`
  - `steroids.drawers.hide`
  - `steroids.drawers.on/off`
- Support for automated UI test runner.

Bugfixes:
- Replacing layers failed when doing the API call from a WebView which
  was not visible, ie. not added to any layer.
  (fixes [#581](https://github.com/AppGyver/steroids/issues/581)).
- Fixed three WebView related memory leaks, which will help overall stability.
- Fixed a crash occurring when onPageLoaded callback was invoked for a
  WebView which had already been killed (affected especially slower devices).
- Fixed a crash when changing orientation too rapidly with Crosswalk
  (fixes [#575](https://github.com/AppGyver/steroids/issues/575))


## 4.0.0-edge1 (2014-10-24): In-place animations

Features:
- In place animations (flip and slide to four directions).
- Complete Layers API
  - `steroids.layers.replace`
  - `steroids.layers.popAll`


## 3.5.4-rc2 (2014-10-23): Fix pushing a preloaded layer

3.5.4-rc2 was released as 3.5.4 (stable).

Bugfixes:
- Pushing a preloaded layer displayed a blank view.
- Destroy splashscreen view after it has been displayed.


## 3.5.4-rc1 (2014-10-21): Splash Screen

Breaking change:
- Native CSS is read from `native-styles/android.css` instead of
  `native-styles/default.css`
  ([#558](https://github.com/AppGyver/steroids/issues/558)).

Features:
- Display Splashscreen on application start.
  - Splashscreen is displayed for three seconds by default and
    then hid automatically.
  - To gain control over when to hide splashscreen, use `steroids.splashscreen.hide()` and set `AutoHideSplashScreen` to false in `config.android.xml`.
- Cordova assets are no longer copied to internal storage
  in Scanner to speed up the application start. Cordova can now only be loaded from `http://localhost/cordova.js`.
- When application is started with a custom schema,
  the value can be read from `window.AG_APP_STARTUP_URL` ([#141](https://github.com/AppGyver/steroids/issues/141)).

Bugfixes:
- Not defining `title` or `id` in for Tab Item in application.coffee caused a crash.
- Cordova's `config.(android.).xml` was not properly applied. This caused problems with plugins depending on it (eg. FileTransfer, Urban Airship)
  (fixes [#564](https://github.com/AppGyver/steroids/issues/564),
   [#533](https://github.com/AppGyver/steroids/issues/533)).
- Drawer in application.coffee caused a crash.
- Certain null attribute values in application.coffee caused a crash.
- WebView touch events are now disabled when opening a new WebView.
  This previously allowed to eg. invoke several subsequent layers.push() method
  calls by repeatedly tapping a button
  (fixes [#539](https://github.com/AppGyver/steroids/issues/539)).


## 3.5.4-edge4 (2014-10-13): Reaching Stable Soon

Features:
- Change the whole Native UI styling at once with `steroids.app.loadTheme()`.
- Return a list of all currently preloaded WebViews with `steroids.app.getApplicationState()`.
- Define a Native CSS `id` in application.coffee for Tabs, to allow convenient
  styling of individual Tab Items (eg. setting the icon individually for each Tab).

Bug fixes:
- Showing the soft keyboard on top layer caused flickering.
- Drawer settings in application.coffee caused a crash.
- Status Bar hide/show and rotation from landscape->portrait caused flickering.
- Sending a Post Message caused the recipient view to flicker over the sender
  view (affected only Chromium runtimes).
- Tab Bar sometimes appeared as empty right after application start.
- API `navigation.bar.show()` is now consistent with iOS:
  - Success callback is invoked.
  - Change default to show navigation bar without animation.
- Navigation Bar title no longer disappears if other buttons are set.

Internal:
- Implementation for Composer required GetNSUserDefaults API


## 3.5.4-edge3 (2014-10-08): Native Styling with CSS

Features:
- Style Native UI elements with CSS (Pixate).
  - Define styles in `dist/native-styles/default.css`.
  - API for `setStyle`, `setClass` and `setId`.
  - Supported elements: Navigation Bar, Buttons, Tab Bar.
- Output WebView console.log messages using INFO log level
  (ie. visible on production builds).
- Remove permission `DOWNLOAD_WITHOUT_NOTIFICATION` which is no longer needed.
- Set WebView default background color to white.
- Load Scanned Application in an emulator without requiring to scan the QR code.
- Implement API for `steroids.tabBar.update`.

Bug fixes:
- Steroids.on event didn't fire properly on 3.5.4-edge2.
- When using Tab Bar, sometimes a wrong WebView is visible with Chromium
  (fixes [#526](https://github.com/AppGyver/steroids/issues/526)).
- Loading.html wasn't displayed after starting the application from Initial View.


## 3.5.4-edge2 (2014-09-25): Initial Drawer

**3.5.4-edge2 was hidden from Build Service on 26th September due to the edge being broken and not firing Steroids ready event.**

Features:
- Drawer can be initialized from application.coffee.
- Support window.AG_* constants
  - AG_CLIENT_VERSION
  - AG_APP_STARTUP_URL (only for Scanner currently)
  - AG_WEBVIEW_UUID
  - AG_WEBVIEW_UDID (legacy attribute, will be removed later)
- Scanner version is the code defined in the Build Service.
- Make Cordova's ScrollEvent class available to Cordova plugins.
- Include hardcoded Open GL 2 version in default Android Manifest for
  Google Maps plugin support. This will be fixed properly by providing this is
  as a user configurable option.

Bug fixes:
- Opening two Steroids layers no longer result in two WebViews being created.
- Preloads are no longer loaded before Initial View is dismissed.
- Sending a post message caused a NPE when application was shutting down.
- Resetting application to initial view caused next initial view dismissal to fail.
- Displaying a WebView no longer causes a nasty blink.
- CordovaWebView#reload() expected by plugins is now implemented.


## 3.5.4-edge1 (2014-09-19): Navigation Bar buttons and Initial View

Features:
- Navigation Bar modification methods available:
  - Back button text can be modified and replaced with an image
  - Back button can be overridden
  - Navigation Bar can have an image as the title
  - Navigation Bar can have multiple custom buttons
    - both image and text are supported
- InitialView can be shown, dismissed and app can be resetted to it
- Status bar onSuccess and onFailure callbacks on show and hide
- Loading.html is shown when WebView is pushing, tabs are loading or a modal is shown.

Known issues:
- Setting a custom back button title makes the nav bar title misalign
- If navigation bar title is set to be an image, it disappears if other buttons have been modified
- Scrolling can be quite clunky at times
- Loading.html does not show after resetting app to InitialView
- Re-download from Scanner crashes the app

## 3.5.3-rc3 (2014-09-16): Return proper 404 errors in http://localhost

Bug fixes:
- Return HTTP 404 Not Found when an asset from http://localhost does not
  exist. Previously "Connection Refused" was the result which caused problems.
  (fixes [#524](https://github.com/AppGyver/steroids/issues/524))


## 3.5.3-rc2 (2014-09-10): Multipage apps with Chromium

Bug fixes:
- Applied a workaround to get multipage support on Chromium
  (closes [#495](https://github.com/AppGyver/steroids/issues/495))

Known issues:
- Viewport size must be defined in the HTML or content will appear as zoomed out
  ([#297](https://github.com/AppGyver/steroids/issues/297))
- Chromium runtime doesn't handle device button events correctly
  ([#519](https://github.com/AppGyver/steroids/issues/519))


## 3.5.3-rc1 (2014-09-09): Styled navigation bar

This is the first release candidate for 3.5.3-stable.

Features:
- Navigation bar looks more native by default.
- Required permissions can be configured in the Build Service
  (closes [#508](https://github.com/AppGyver/steroids/issues/508))

Bug fixes:
- URLs with a double slash no longer give an error message,
  eg. `http://localhost//index.html` (fixes [#514](https://github.com/AppGyver/steroids/issues/514))
- Scanned URL is correctly remembered when opening a previously scanned app
  (fixes [#513](https://github.com/AppGyver/steroids/issues/513))
- Back button no longer wraps into two lines on small screens
  (fixes [#512](https://github.com/AppGyver/steroids/issues/512))


## 3.5.3-edge4 (2014-09-04): Styled scanner

Features:
- Scanner shares similar outlook with the AppGyver iOS client.
- API for visibilityState returns values according to the WebView's visibility
- Tab bar is displayed on the bottom by default to allow better multiplatform
  consistency. Tab bar position can be changed in the future in `application.coffee`
  and with `steroids.tabBar.update`.
- WebViews have unique identifiers (UUID) available API calls.
- Crosswalk runtimes updated to 8.37.189.7 with Chromium M37.0.2062.94 (closes [#485](https://github.com/AppGyver/steroids/issues/485))

Bug fixes:
- Back button now closes all open modals before exiting the app (fixes [#505](https://github.com/AppGyver/steroids/issues/505)).
- WebView transitions now work with Android 4.0.
- Tab bar no longer gets misaligned on Android 4.0 after orientation change (fixes [#494](https://github.com/AppGyver/steroids/issues/494)).
- Preloaded views can be displayed multiple times (fixes [#510](https://github.com/AppGyver/steroids/issues/510)).
- Navigation bar's visible size stays the same although different devices have
  different pixel-densities.


## 3.5.3-edge3 (2014-09-01): Navigation bar

New naming convention for edge versions: the "p" is now dropped out because too many people
confused stable patch level releases (3.5.2-p2) with edges (3.5.2-edge-p2).
This caused wrong version numbers being reported in bug reports.

Features:
- Navigation bar
  - Back button returns to the previous WebView
  - API calls
    - show / hide the navigation bar
    - set the navigation bar title

Bug fixes:
- Scanner intelligently selects the correct IP address from the scanned
  QR code (fixes [#302](https://github.com/AppGyver/steroids/issues/302))
- Tab Bar position is remembered when switching the frontmost activity,
  for example: pause/resume the app, open the camera.
  (fixes [#503](https://github.com/AppGyver/steroids/issues/503))
- Exiting the app no longer causes Illegal State Exception
  (fixes [#504](https://github.com/AppGyver/steroids/issues/504))
- Scanner no longer runs out of memory with a one second polling interval
  (fixes [#359](https://github.com/AppGyver/steroids/issues/359))

## 3.5.3-edge-p2 (2014-08-26)

Bug fixes:
- Fix crash which occurred if Tab Bar wasn't defined in application.coffee ([#497](https://github.com/AppGyver/steroids/issues/497))
- Implement rest of Chromium WebView APIs required by Cordova

## 3.5.3-edge-p1 (2014-08-22): Initial MPA and Updated Chromium

Features:
- Initial support for multi-page applications:
  - Views can be pushed/popped in the layer stack.
  - Modal can be displayed and hid.
  - All modals can be closed at once.
  - Basic animation for layer transitions.
  - Preloaded views.
  - Tab bar for selecting the current set of views on the screen.
  - Back button navigates back in the current view stack.
- Completely revamped Chromium internals
  - Chromium is now provided by the [Crosswalk Project](https://crosswalk-project.org/).
  - Chromium updated to M37 using Crosswalk-8.
- Chromium runtime supports loading project assets from http://localhost.
- Communicate between WebViews using JavaScript post messages.

Known issues:
- Chromium runtime supports only Single-Page apps ([#495](https://github.com/AppGyver/steroids/issues/495))
  - Vote [issue XWALK-2012](https://crosswalk-project.org/jira/browse/XWALK-2012) on Crosswalk Jira to let them know You want multi-page apps.
- Android 4.0 issues:
  - Tab bar is not displayed correctly ([#494](https://github.com/AppGyver/steroids/issues/494))
  - Cordova plugins for Steroids Addons do not initialize correctly ([#493](https://github.com/AppGyver/steroids/issues/493))
- Android 2.3 is no longer supported starting from 3.5.3
  - Release 3.5.2 will be stay available in Build Servier as a support release for Android 2.3.


## 3.5.2-edge-p3 (2014-08-11)

Features:

- A Steroids app can now send logs to Steroids CLI via `steroids.logger.log`.
- Opening a link with the `appgyver://` schema will open the Fresh Android application.
- An AppGyver Cloud QR code can be used to load a Steroids app.
- An event (`steroids.keyboard.on` `actionButtonPressed`) is now dispatched when the Go button is pressed on the Android software keyboard.

Bug fixes:

- Most of Android permissions required by Scanner are marked as optional, which allows e.g. downloading the Scanner from Google Play even if the device doesn't have Camera.
- Fixed crash caused by the QR code reader timing out or returning corrupted data.
- Previously opened WebViews are properly closed when Scanned Steroids application is reloaded.
- Fixed compatibility with the [email composer Cordova plugin](https://github.com/AppGyver/email-composer/).


## 3.5.2-edge-p2 (2014-07-31)

Features:
- Facebook SDK is included by default (will be optional later), which allows the official
  Cordova Facebook plugin to compile.



## 3.5.2-edge-p1 (2014-07-31)

Features:
- Android keyboard's Go button triggers an event that can be used on Javascript side.
- WebKit runtime supports initial_eval_js_string.
- Updated media-capture plugin to 0.3.1
- Updated media plugin to 0.2.11
- Updated file-transfer plugin to 0.4.4
- Updated file plugin to 1.2.0
- Complete support for Cordova's onMessage (required for plugins).
- Steroids application can send logs to Steroids CLI (or any endpointUrl)


Bug fixes:
- navigator.app.exitApp() now quits the application.
- Previously opened WebViews are now closed after a scanned application is restarted.
