# JavaScript Development Environment
[![Build Status](https://travis-ci.org/mtwilliams5/js-dev-env.svg?branch=master)](https://travis-ci.org/mtwilliams5/js-dev-env)

This JavaScript Development Environment was created during the Pluralsight Course with Cory House. 
It's base is [**Node 6**](https://nodejs.org/), using **NPM** as the package manager to load the dependencies.

# Key Configuration Decisions
* **Editor Config**
This environment uses [**EditorConfig**](http://editorconfig.org/) to define the coding style. [**VSCode**](https://code.visualstudio.com/) is my editor of choice, but it should work with any [compatible editor](http://editorconfig.org/#download).
* **Package Management**
This environment uses [**NPM**](https://www.npmjs.com/) as the package manager with [**NSP**](https://www.npmjs.com/package/nsp) to maintain the security of the code. NPM also handles script-based automation.
* **Development Web Server**
[**Express**](http://expressjs.com/) is used for both the development and the (local-only) production web server.
* **Transpiler**
[**Babel**](https://babeljs.io/) is used to transpile the code down to ES5 standards, enabing the source to be written in ES6.
* **Bundler**
[**Webpack**](https://webpack.github.io/) is used to bundle the code to reduce download size, with third-party (vendor) JS and all CSS files separated from the core app JS. Sourcemaps are produced to enable debugging in the browser.
* **Linting**
Linting is handled by [**ESLint**](http://eslint.org/), included as an NPM dependency rather than installed directly into the editor, to ensure consistent linting for all uses of the environment. *ESLint* is set to watch files to alert to linting errors and warnings on file save. *(NOTE: For users of Windows Subsystem Linux, the Creators Update is required to enable file-watching functionality)*
* **Testing**
[**Mocha**](https://mochajs.org/) is used as the primary testing framework, using [*Chai*](http://chaijs.com/) as its assertion library, and [*JSDOM*](https://www.npmjs.com/package/jsdom) as a helper library to enable DOM testing without a browser. Testing is set up with file-watching capability, to run on every save and ensure failures are captured as soon as they are caused. *(NOTE: For users of Windows Subsystem Linux, the Creators Update is required to enable file-watching functionality)*
* **HTTP Calls & Mock API**
Browser-side HTTP Calls are handled using *Fetch* with polyfill to ensure that the function works on older browsers. [**Nock**](https://www.npmjs.com/package/nock) is used to mock an API to enable testing against it without linking up to a production API, using [*Schema Faker*](http://json-schema-faker.js.org/#gist/eb11f16c9edccf040c028dc8bd2b1756) and *Express*.
* **Error Logging**
Error logging in the production environment is handled by [**TrackJS**](https://trackjs.com/).
* **Continuous Integration**
Continuous Integration scripts have been set up for [**TravisCI**](https://travis-ci.org/) (Linux) and [**Appveyor**](https://www.appveyor.com/) (Windows), with builds configured to watch the GitHub repo for changes.
* **Deployment**
Deployment of the production app post-build is handled through [**Surge**](https://surge.sh/).

## Development Dependencies
| **Dependency**              | **Use**                                                                                                   |
| --------------------------- | --------------------------------------------------------------------------------------------------------- |
| babel-cli                   | Babel Command line interface                                                                              |
| babel-core                  | Babel Core for transpiling the new JavaScript to old                                                      |
| babel-loader                | Adds Babel support to Webpack                                                                             |
| babel-preset-latest         | Babel preset for running all the latest standardized JavaScript features                                  |
| babel-register              | Register Babel to transpile our Mocha tests                                                               |
| cheerio                     | Supports querying DOM with jQuery like syntax - Useful in testing and build process for HTML manipulation |
| cross-env                   | Cross-environment friendly way to handle environment variables                                            |
| css-loader                  | Add CSS support to Webpack                                                                                |
| eslint                      | Lints JavaScript                                                                                          |
| eslint-plugin-import        | Advanced linting of ES6 imports                                                                           |
| eslint-watch                | Add watch functionality to ESLint                                                                         |
| eventsource-polyfill        | Polyfill to support hot reloading in IE                                                                   |
| expect                      | Assertion library for use with Mocha                                                                      |
| express                     | Serves development and production builds                                                                  |
| extract-text-webpack-plugin | Extracts CSS into separate file for production build                                                      |
| file-loader                 | Adds file loading support to Webpack                                                                      |
| jsdom                       | In-memory DOM for testing                                                                                 |
| mocha                       | JavaScript testing library                                                                                |
| npm-run-all                 | Display results of multiple commands on single command line                                               |
| open                        | Open app in default browser                                                                               |
| rimraf                      | Delete files                                                                                              |
| style-loader                | Add Style support to Webpack                                                                                              |
| surge                       | Deploy the production code to the web                                                                                              |
| url-loader                  | Add url loading support to Webpack                                                                        |
| webpack                     | Bundler with plugin system and integrated development server                                              |
| webpack-dev-middleware      | Adds middleware support to webpack                                                                        |
| webpack-hot-middleware      | Adds hot reloading to webpack                                                                             |
