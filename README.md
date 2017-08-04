# iOS App Creation Steps through ionicFramework

#### INTRODUCTION
This repository serves as personal notes on the steps required to create iOS
apps through ionic Framework.  
The steps are grouped as follows:
* Development Steps
* Provisioning Steps
* Packageing Steps

#### REQUIREMENTS
You will need the following to complete the task:
* OpenSSL (to create CSRs and keys)
* Development environment:
    * Ionic Creator Account (if you want to develop through the cloud) or
    * Simply install the following and start developing from your machine:
        * [Node.JS](https://nodejs.org/en/)
        * [Ionic](http://ionicframework.com/)
        * Cordova (for native functions implementation)
        ```command-line
        npm install -g ionic cordova
        ```
* Apple Developer Account ($99/yr) obviously to upload and test your application
* Google Console account ($25/yr)
* For push notifications, checkout the following:
	* https://onesignal.com
	* firebase
	* Ionic Cloud
* Setup a Firebase (google) account for tracking crashes and making push requests
    * take note of the Sender ID
    * install firebase on your ionic
    ```command-line
    ionic cordova plugin add cordova-plugin-firebase
    npm install --save @ionic-native/firebase
    ```
    * Install other cordova plugins
    ```command-line
    ionic cordova plugin add cordova-clipboard
    npm install --save @ionic-native/clipboard
    ionic cordova plugin add cordova-plugin-x-socialsharing
    npm install --save @ionic-native/social-sharing
	npm install @ionic/cloud-angular --save
	cordova plugin add ionic-plugin-deploy --save
	ionic cordova plugin add cordova-plugin-actionsheet
	npm install --save @ionic-native/action-sheet

    ```
* Good text editor
    * Atom
    * Brackets
    * Notepad++
	* MS Visual Code
* Mac Machine (or Mac Virtual Machine ;)), to load your IPA into developer account and test on iOS Simulator
    * an [App Specific Password](https://appleid.apple.com) if you use two factor authentication on your account
* Android Stuff for Android deployement and testing
    * [Java JDK](http://www.oracle.com/technetwork/java/javase/downloads/index-jsp-138363.html)
    * [Android Studio](https://developer.android.com/studio/index.html)
    * [Updated Android SDK tools](https://developer.android.com/studio/intro/update.html)
* Splash Screen and Icons

## Take note of
#### for IOS
* Your apple developer account id and Password
* App Identifier Name
* App Prefix (not sure if it is important)
* App Name
*


#### for android
* Install JDK
* create keystore
    * `keytool -genkey -v -keystore f6sny.keystore -alias f6sny_app -keyalg RSA -keysize 2048 -validity 10000`
    * memorize the Password
* Not much else, I just used the keystore while compiling the app. Nothing in google playstore.
* Just filled a profile for the app in google console and that was it.


## App Development Stage
Here are the steps to start developing your app
* For Typescript backend `ionic start yourprojectname tabs`
* For JavaScript backend `ionic start yourprojectname tabs –type ionic1`
  (for JS support, ionic 2 is strictly Typescript and most of us hate that)



## App Provisioning Stage
These steps are the minimum requirements for provisioning (for usage or testing) your app.

* Generate a private RSA Key `openssl genrsa -out f6sny.key 2048`
* Create a CSR `openssl req -new -key f6sny.key -out f6sny.certSigningRequest`
    * Do not Enter Email Address
* Download your certificate from apple developer website
* Convert the Certificate to a P12 File
```command-line
openssl x509 -inform DER -outform PEM -in ios_distribution.cer -out ios_distribution.cer.pem
openssl pkcs12 -export -inkey f6sny.key -in ios_distribution.cer.pem -out Certificates.p12
```
    * Choose and remember password for the p12 certificate (will be used in creator.ionic page)
* Create provisioning profile
* Download your ipa from ionic
	* To automatically create your IPA or APK from CLI, use `ionic cordova build --release android` (replace android with ios for iphone)
* Create app in itunesconnect
* open xCode
* open application loader and upload your file
* head to itunes connect and finish the write-ups
* submit for review
* Develop your artwork using [iOS 10 App Icon Template PSD/Sketch](http://www.everyinteraction.com/resources/ios-10-app-icon-template-psd-sketch/)
	* Or, simply create your `splash.png` and `icon.png`, place them in the resources folder and run `ionic cordova resources`
* Prepare screenshots for iPad and iPhone
* Prepare promotional text
* Prepare description
* Prepare search keywords
* Prepare notes for apple review
* Wait 3 days for review
* Utilize Ionic Delpoy to save some time [Get Started With Ionic Services: Deploy](https://code.tutsplus.com/tutorials/get-started-with-ionic-services-deploy--cms-28827)

> Reference: [Ionic Publishing Guide](http://ionicframework.com/docs/v1/guide/publishing.html)



## Build your app
#### Through ionic cloud
* Create a security profile in your cloud account [Security Profiles](https://docs.ionic.io/services/profiles/)
* Request the build
	* iOS `ionic package build ios --profile PROFILE_TAG --prod --release` (ensure profile tag is all lowercase)
	* Android `ionic package build android --profile PROFILE_TAG --prod --release`
* Check build status `ionic package list`
* Download your build `ionic package download BUILD_ID` (will download to your app directory)

#### Through CLI
* For Android
It is a normal process, just check the docs
* For iOS
You would need a mac machine, maybe through a virtual box?


## Tips and Tricks
#### App Development
These are some tips that you might or might not need while developing your application
* In development environment, while developing your API:
    * Use HTTPS for iOS as HTTP is not accepted.
    * add the following code to your PHP files to enable cross-origin requests:
    ```PHP
    header("Access-Control-Allow-Origin: *");
    ```
    * to start (test) your app `ionic serve`
	* to rtl support, start by setting the html `lang` and `dir` attributes of the html element


#### App Provisioning
* Test your app on emulator `ionic cordova build android` and `ionic cordova run android`
* If any problem encountered during emulation or build, try re-build
  ```command-line
	  ionic cordova platform rm android
	  ionic cordova platform add android
  ```
  * Remove development plugins `ionic cordova plugin rm cordova-plugin-console`
* Make sure to configure `config.xml` correctly, refer to: [cordova apache](http://cordova.apache.org/docs/en/latest/config_ref/index.html) for details.
	* name attribute would be tha apk name and ipa name, and might be used for store title






## References
> [ionic Framework Docs](https://ionicframework.com/docs)
    * [ionic deployment manual](http://ionicframework.com/docs/intro/deploying/)
> [AngularJS Basics](https://www.w3schools.com/angular/default.asp)
> [AngularJS Docs](https://docs.angularjs.org/api)
> [Ionic Publishing Guide](http://ionicframework.com/docs/v1/guide/publishing.html)
> [Ionic Framework: A definitive 10,000 word guide](https://www.pluralsight.com/guides/front-end-javascript/ionic-framework-a-definitive-10-000-word-guide)
> [Creating a Sliding Introduction Component in Ionic 2 & 3](https://www.joshmorony.com/creating-a-sliding-introduction-component-in-ionic-2/)

## MAINTAINERS
#### Current Maintainers:
* **Mohannad F. Otaibi** (@buFai7an) - http://www.mohannadotaibi.com
* **Your name?** - email me at mohannadotaibi + gmail.com

#### Sponsored by:
* 6 Degrees Technologies - http://www.6d.com.sa  
  Specialized in, simply, Technologies.

## COPYRIGHTS
No copyrights at all, I just collected all of this from all over the internet (which is a public place) and published it here for my own use and for your use.
