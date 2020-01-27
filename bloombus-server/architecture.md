# Architecture

BloomBus-Server provides backend services for making modifications to the Firebase database in real-time. Largely this will serve as the basis for performing ETA predictions using a TensorFlow model, but for now it is largely used for housekeeping procedures.

Originally, BloomBus-Server was a bundle of Firebase Cloud Functions, which were set up to be triggered by updates on various references in the Firebase Realtime Database. This was later converted to localized functions running in a Node.js script \(written in TypeScript\) to reduce overhead from continuously firing serverless functions essentially once a second, remove dependence on cloud infrastructure and its potential associated costs, and to make it easier to test and develop the services that BloomBus-Server provides.

BloomBus-Server also serves as the webserver for BloomBus' admin dashboard, which is delivered via an Express.js server over port 8080.

The Express.js server also provides REST API services on port 8080, additional information in the [REST API](rest-api.md) section.

