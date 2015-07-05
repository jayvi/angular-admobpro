AdMob Pro for AngularJS
==========

AngularJS extension on top of [AdMob Pro Cordova Plugin](https://github.com/floatinghotpot/cordova-admob-pro)

# Installation

Firstly you need to install [AdMob Pro](https://github.com/floatinghotpot/cordova-admob-pro) on your Cordova Project.

    cordova plugin add cordova-plugin-admobpro

Then you can proceed installing angular-admobpro using bower:

    bower install angular-admobpro --save

Then add the sources to your code (adjust paths as needed) after adding the dependencies for Angular first:

```html
    <script src="../bower_components/angular/angular.min.js"></script>
    <script src="/bower_components/angular-chart.js/dist/angular-chart.js"></script>
```


# How to use with Ionic Framework

    angular.module('yourApp', ['ionic', 'admob'])
        .run(function($rootScope, $state, $log, $adMob) {

            $ionicPlatform.ready(function() {
                // AdMob
                if(window.AdMob) {
                    var admobid;

                    if (device.platform == "Android") {
                        admobid = { // for Android
                            banner: 'ca-app-pub-your-ad-key',
                            interstitial: 'ca-app-pub-your-ad-key'
                        };
                    } else {
                        admobid = { // for iOS
                            banner: 'ca-app-pub-your-ad-key',
                            interstitial: 'ca-app-pub-your-ad-key'
                        };
                    }

                    $adMob.createBanner( {
                        adId: admobid.banner,
                        autoShow: true,
                        bgColor: 'black',
                        position: $adMob.position.BOTTOM_CENTER
                    });

                    $adMob.prepareInterstitial({
                        adId: admobid.interstitial,
                        autoShow: false
                    });
                }
            });
        });

