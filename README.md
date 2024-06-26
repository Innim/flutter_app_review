Fork of [Flutter Community: app_review](https://github.com/fluttercommunity/app_review) with updated dependencies.

[![app_review](https://img.shields.io/pub/v/app_review_plus.svg)](https://pub.dev/packages/app_review_plus)

# app_review_plus

![alt text](https://github.com/Innim/flutter_app_review/blob/master/screenshots/IMG_0024.PNG)

Online Demo: https://fluttercommunity.github.io/app_review/

## Description
Flutter Plugin for Requesting and Writing Reviews in Google Play and the App Store. Apps have to be published for the app to be found correctly.

## How To Use
It's important to note that the App ID must match the App ID in Google Play and iTunes Connect. This can be changed in the Info.plist on iOS and app/build.gradle on Android. You will use this App ID for other services like Firebase, Admob and publishing the app. 

#### Android
Opens In App Review but only if Play Services are installed on the device and the App is downloaded through the Play Store. Check out the [official documentation](https://developer.android.com/guide/playcore/in-app-review).

#### iOS
iOS manages the pop-up requesting review within an app. You can call the code through `AppReview.requestReview` and if the user has "rate in apps" turned on, iOS will send "the request for the review" pop up. This is the required way for requesting reviews after iOS 10.3.

In debug mode it will always display. In apps through TestFlight, the `AppReview.requestReview` does nothing.

``` dart
import 'dart:io';
import 'package:app_review/app_review_plus.dart';
import 'package:flutter/material.dart';

  @override
  void initState() {
    super.initState();
    if (Platform.isIOS) {
      AppReview.requestReview.then((onValue) {
        print(onValue);
      });
    }
  }
```

## What is onValue value?

Just a sanity check to make sure there were no errors.

### Android

You could store a timestamp to know when to call again.

### iOS

It doesn't really matter.
