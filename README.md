# Rater
This is the source code for version 2 of the Wikipedia userscript [Rater](https://en.wikipedia.org/wiki/User:Evad37/rater).
**This is currently *pre-alpha software*. It is not fully functional (and perhaps not even mostly functional)**

## Installation instructions and user guide
- Version 1: See [https://en.wikipedia.org/wiki/User:Evad37/rater](https://en.wikipedia.org/wiki/User:Evad37/rater).
- Version 2: Not yet written, but will likely be similar for the end user.

## Repository structure
- `index.js` is the main entry point, written in ES5. This is published to [User:Evad37/rater.js](https://en.wikipedia.org/wiki/User:Evad37/rater.js)
- `index-sandbox.js` is the equivalent entry point for the sandbox version of the script, also written in ES5. This is published to  [User:Evad37/rater/sandbox.js](https://en.wikipedia.org/wiki/User:Evad37/rater/sandbox.js)
- `rater-src\` contains the main source code for the app, split into modules, which may be written in ES6. Code here can assume that the ResourceLoader modules specified in the above files have been loaded and that the DOM is ready.
   - `App.js` is the entry point
   - Related code should be placed in the same module.
   - Small pieces of code, not particularly related to anything, can be placed in `rater-src\util.js`
- The source code is bundled, transpiled, and minified using `npm run build`. This writes two files to the `dist\` directory:
   - `dist\rater.js` contains bundled and transpiled code, with a source map. It is published to [User:Evad37/rater/sandbox/app.js](https://en.wikipedia.org/wiki/User:Evad37/rater/sandbox/app.js), for testing/debugging purposes.
   - `dist\rater.min.js` is the minified version.  It is published to [User:Evad37/rater/app.js](https://en.wikipedia.org/wiki/User:Evad37/rater/app.js)  (the *live version* of the userscript), once the sandbox version has been adequately tested.
### Tooling
- **eslint** for ES6 linting
- **jshint** for ES5 linting ([ESLint doesn't support override for ecmaVersion](https://github.com/sindresorhus/eslint-config-xo/issues/16#issuecomment-190302577))
- **browserify** with **babelify** for bundling, transpiling, and source-mapping
- **uglifyjs** for minifying

## TODO

 - [ ] Finish writing app (min viable product - same or better functionality than v1) 
    - OOUI window for the main dialog
    - ...etc...
 - [ ] Investigate unit testing
    - Is node-based unit testing even possible, given the reliance on globals like `mw` and `OO`?
    - Look at how v1 is using QUnit unit testing. Maybe replicate or iterate on that.
    - Or maybe have QUnit tesing inside the app source code, that gets run if the url contains a query parameter such as `&testrater=1`?
- [ ] Improve documentation
- [ ] ... probably other things too - finish off this list, and/or put issues on the github page.
### Roadmap
- [ ] Complete the v2 rewrite
- [ ] Get beta testers to try out the new version. Fix/adjust things as they get reported.
- [ ] Release the new version generally.