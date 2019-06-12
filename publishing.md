# Publishing

BloomBus-Tracker-Android is published to the Google Play Store under an Internal Testing release. This allows the app to be private with a specified list of emails that are registered as testers, including any users that follow the opt-in link.  
BloomBus-Client is on its way to being deployed to the Google Play Store now that it supports publishing Progressive Web Apps. PWAs are supported through a new API added in Chrome 72 called "Trusted Web Activities". John Gibson started working on publishing the BloomBus-Client PWA by following [this guide by @firt on Medium](https://medium.com/@firt/google-play-store-now-open-for-progressive-web-apps-ec6f3c6ff3cc), although [this guide from fireship.io](https://fireship.io/lessons/pwa-to-play-store/) looks even more thorough. The TWA API allows for some important features such as adding an Android Wear companion app and delivering native push notifications.

To sign releases for BloomBus-Tracker-Android, the Android keystore for the project needs to be acquired from the Firebase storage bucket which you can access through Firebase Console, and should be put in the `/app` directory of the repo. You should also have a gradle.properties file which holds the values for the various keystore secrets, and these values can be acquired by asking any of the project admins on the Discord chat.

