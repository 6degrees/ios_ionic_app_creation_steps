# iOS App Creation Steps through ionicFramework

#### INTRODUCTION
This repository serves as personal notes on the steps required to create iOS
apps through ionic Framework.  
The steps are grouped as follows:
* Development Steps
* Provisioning Steps

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
* Good text editor
    * Atom
    * Brackets
    * Notepad++
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
* Develop your artwork using [iOS 10 App Icon Template PSD/Sketch](http://www.everyinteraction.com/resources/ios-10-app-icon-template-psd-sketch/)
* Prepare screenshots for iPad and iPhone
* Prepare promotional text
* Prepare description
* Prepare search keywords
* Prepare notes for apple review


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

#### Tips for App Development Stage
These are some tips that you might or might not need while developing your application
* In development environment, while developing your API:
    * Use HTTPS for iOS as HTTP is not accepted.
    * add the following code to your PHP files to enable cross-origin requests:
    ```PHP
    header("Access-Control-Allow-Origin: *");
    ```
    * to start (test) your app `ionic serve`

## App Provisioning Stage
These steps are the minimum requirements for provisioning (for usage or testing) your app.
* Step 1
* Step 2

#### Tips and Tricks for App Provisions

## References
* [ionic Framework Docs](https://ionicframework.com/docs)
    * [ionic deployment manual](http://ionicframework.com/docs/intro/deploying/)
* [AngularJS Basics](https://www.w3schools.com/angular/default.asp)
* [AngularJS Docs](https://docs.angularjs.org/api)
* []()
* []()

## MAINTAINERS
#### Current Maintainers:
* **Mohannad F. Otaibi** (@buFai7an) - http://www.mohannadotaibi.com
* **Your name?** - email me at mohannadotaibi + gmail.com

#### Sponsored by:
* 6 Degrees Technologies - http://www.6d.com.sa  
  Specialized in, simply, Technologies.

## COPYRIGHTS
No copyrights at all, I just collected all of this from all over the internet (which is a public place) and published it here for my own use and for your use.
