# Publishing

BloomBus-Tracker-Android is published to the Google Play Store under an Internal Testing release. This allows the app to be private with a specified list of emails that are registered as testers, including any users that follow the opt-in link.  
BloomBus-Client is on its way to being deployed to the Google Play Store now that it supports publishing Progressive Web Apps. PWAs are supported through a new API added in Chrome 72 called "Trusted Web Activities". John Gibson started working on publishing the BloomBus-Client PWA by following [this guide by @firt on Medium](https://medium.com/@firt/google-play-store-now-open-for-progressive-web-apps-ec6f3c6ff3cc), although [this guide from fireship.io](https://fireship.io/lessons/pwa-to-play-store/) looks even more thorough. The TWA API allows for some important features such as adding an Android Wear companion app and delivering native push notifications.

To sign releases for BloomBus-Tracker-Android, the Android keystore for the project and the gradle.properties which holds the values for the various keystore secrets are needed, and can be found in the \#devs-resources channel in the Discord server, accessible to those with the "dev" role.

