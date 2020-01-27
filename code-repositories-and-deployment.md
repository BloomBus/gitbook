---
description: Current code repository usage & deployment information.
---

# Code Repositories & Deployment

## Code Repositories

All 3 of the project's code repos are on GitHub under the [BloomBus](https://github.com/BloomBus) organization.

* [BloomBus/BloomBus-Tracker-Android](https://github.com/BloomBus/BloomBus-Tracker-Android)
* [BloomBus/BloomBus-Tracker](https://github.com/BloomBus/BloomBus-Tracker) **\(deprecated\)**
* [BloomBus/BloomBus-Client](https://github.com/BloomBus/BloomBus-Client)
* [BloomBus/BloomBus-Server](https://github.com/BloomBus/BloomBus-Server)
* [BloomBus/gitbook](https://github.com/BloomBus/gitbook) — the repository for this GitBook

For more information about any of these repos, visit their respective pages within this GitBook.

Currently,  BloomBus-Client is deployed to Heroku at [https://bloombus.herokuapp.com](https://bloombus-tracker.herokuapp.com).

## Deployment

#### What's Heroku?

Heroku is a "cloud application platform". In short, it provides a CLI tool to add a git remote to your project, and whenever new changes are pushed to that remote, it will analyze the project, try and determine a "buildpack" to run to build the project, and stand it up on one of Heroku's servers.

BloomBus-Client was created using the **create-react-app** package from Facebook, which is a very popular tool for bootstrapping a basic React application without having to write all of the boilerplate yourself. The [ community-made buildpack](https://github.com/mars/create-react-app-buildpack) for create-react-app apps on Heroku is used for deployment.

