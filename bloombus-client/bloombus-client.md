---
description: A description of the architecture for the BloomBus-Client project.
---

# Architecture

[GitHub Link](https://github.com/BloomBus/BloomBus-Client)

At the root of the BloomBus-Client codebase, it is split into 2 folders, **`/public`** and **`/src`**.  As is typical with many web application codebases, the **`/public`** directory is used to dump the processed output of the project's build process, and acts as the root that should be served over a webserver. **`/src`** is the home of all files that are to be fed into the project's build process. This build process is initiated by executing **`npm start`** in the project's root directory. The details of this build process is defined in the **package.json** file also at the project's root.

If you are unfamiliar with **Node.js** and it's Node Package Manager \(**NPM**\), then it is very imortant to do some introductory reading. My recommendation would be to take a look at NPM's documentation here:

{% embed url="https://docs.npmjs.com/getting-started/what-is-npm" %}

Within the **`/src`** directory, there are several files \(App.js, App.css, and index.js\) that bootstrap the React app together.

Also within this folder is the **`/components`** directory. Each React component gets its own folder, which stores the component definition file \(\*.jsx\), any test scripts written for the component \(\*.test.js\), and any CSS specific to that component.

Back in the **`/src`** directory, there is also a **`/utils`** directory. Any variables and functions that are not specific to a particular component and that are frequently reused across separate files are put in the **`/utils`** directory and exported as an [ES6 module](https://alligator.io/js/modules-es6/), and imported where needed.



