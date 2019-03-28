---
description: Ideas for migrating from cloud to self-hosted services if needed
---

# Cloud → Self-hosted

The project in its early stages has depended on cloud services to be able to rapidly prototype software components, namely the services offered by Firebase, but also the webapp hosting & deployment through Heroku.  
BloomBus' real-time database storage and synchronization between the database, serverside scripting and clients are all done through Firebase's Realtime Database service.

There are numerous operations that need to be performed on the database as data is altered in real-time \(such as when a bus' coordinates are updated\) which at the moment include the `reapOldShuttles` and `triggerStationProximity` functions. These were originally deployed as serverless functions through Firebase's Cloud Functions service, but John Gibson converted these to to local functions to be run on a typical Node.js server, which at the time of this writing is the current state of the BloomBus-Server repo.  
  
As previously mentioned, BloomBus-Client is deployed to Heroku using webhooks for new commits to BloomBus-Client Github repo using the [third-party create-react-app buildpack](https://elements.heroku.com/buildpacks/mars/create-react-app-buildpack).

If there is desire to make the operation of BloomBus independent of Cloud services, then the most promising alternative appears to be the [Parse Server](http://parseplatform.org/) platform. Since it is meant to be attached  It has over 30,000 stars on GitHub and has received updates to include [Live Queries](http://docs.parseplatform.org/parse-server/guide/#live-queries) which enable the real-time functionality via a model-subscriber scheme that Firebase provides. There's also [ParseReact](https://github.com/parse-community/ParseReact) which could make the data management more straightforward. Assuming that BloomBus-Client is already being run by a university server by just calling `npm start` on the project directory, then to integrate BloomBus-Server and the real-time database you would likely need to figure out how to eject BloomBus-Client from create-react-app and host it on an Express.js webserver that is shared between BloomBus-Client and the Parse Server.

