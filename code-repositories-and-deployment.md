---
description: Current code repository usage & deployment information.
---

# Code Repositories & Deployment

All 3 of the project's code repos are on GitHub under the [BloomBus](https://github.com/BloomBus) organization.

* [BloomBus/BloomBus-Tracker](https://github.com/BloomBus/BloomBus-Tracker)
* [BloomBus/BloomBus-Client](https://github.com/BloomBus/BloomBus-Client)
* [BloomBus/BloomBus-Server](https://github.com/BloomBus/BloomBus-Server)
* [BloomBus/gitbook](https://github.com/BloomBus/gitbook) — the repository for this GitBook

For more information about any of these repos, visit their respective pages within this GitBook.

At the current moment,  BloomBus-Client and BloomBus-Tracker are deployed to Heroku at [https://bloombus.herokuapp.com](https://bloombus-tracker.herokuapp.com) and [https://bloombus-tracker.herokuapp.com](https://bloombus-tracker.herokuapp.com).

## What's Heroku?

Heroku is a "cloud application platform". In short, it provides a CLI tool to add a git remote to your project, and whenever new changes are pushed to that remote, it will analyze the project, try and determine a "buildpack" to run to build the project, and stand it up on one of Heroku's servers.

For **BloomBus-Tracker**, that project is a simple HTML5 project with just an index.html, some CSS, and a JavaScript script to run. In order to deploy this on Heroku, since Heroku does not have a buildpack for static HTML projects, I have added an index.php file that redirects to the index.html. Because of this file being present, Heroku detects the project as a PHP project and builds it accordingly.

For **BloomBus-Client**, that project is a Node.js application. It was also created using the **create-react-app** package from Facebook, which is a very popular tool for generating a basic React.js application without having to write all of the boilerplate yourself. There is a[ community-made buildpack](https://github.com/mars/create-react-app-buildpack) for Heroku specifically for create-react-app that I have used to resolve some build errors when pushing to Heroku.

