---
description: Instructions for running BloomBus-Server code in a dev environment.
---

# Developing Locally

After cloning the repository and running `npm install`, the server can be started by running `npm start`. The server will serve the production version of the admin dashboard located in `/client/build/` over port **8080** and the REST API services at `/api/*`. 

To run the dev server to work on the admin dashboard with live-reloading \(recommended\), first start up BloomBus-Server at the root, then enter the `/client` directory and run `npm start`. The dev server will launch over port **3000**, and as specified in the `package.json` in the client directory all requests will be forwarded via proxy to port  8080.

