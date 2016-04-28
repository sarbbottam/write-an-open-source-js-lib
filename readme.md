Reference for [How to Write an Open Source JavaScript Library](https://egghead.io/series/how-to-write-an-open-source-javascript-library)
---

The purpose of this document is to serve as a reference for:

[How to Write an Open Source JavaScript Library](https://egghead.io/series/how-to-write-an-open-source-javascript-library) course by [Kent C. Dodds](https://github.com/kentcdodds)

Watch the series at [egghead.io](https://egghead.io/series/how-to-write-an-open-source-javascript-library), if you haven't.

---

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Introduction to How to Write an Open Source JavaScript Library](#introduction-to-how-to-write-an-open-source-javascript-library)
- [Setting up GitHub](#setting-up-github)
- [Configuring npm and creating a package.json](#configuring-npm-and-creating-a-packagejson)
- [Creating the library and adding dependencies](#creating-the-library-and-adding-dependencies)
- [Pushing to GitHub](#pushing-to-github)
- [Publishing to npm](#publishing-to-npm)
- [Releasing a version to GitHub](#releasing-a-version-to-github)
- [Releasing a new version to npm](#releasing-a-new-version-to-npm)
- [Publishing a beta version](#publishing-a-beta-version)
- [Setting up Unit Testing with Mocha and Chai](#setting-up-unit-testing-with-mocha-and-chai)
- [Unit Testing with Mocha and Chai](#unit-testing-with-mocha-and-chai)
- [Automating Releases with semantic-release](#automating-releases-with-semantic-release)
- [Writing conventional commits with commitizen](#writing-conventional-commits-with-commitizen)
- [Committing a new feature with commitizen](#committing-a-new-feature-with-commitizen)
- [Automatically Releasing with TravisCI](#automatically-releasing-with-travisci)
- [Automatically running tests before commits with ghooks](#automatically-running-tests-before-commits-with-ghooks)
- [Adding code coverage recording with Istanbul](#adding-code-coverage-recording-with-istanbul)
- [Adding code coverage checking](#adding-code-coverage-checking)
- [Add code coverage reporting](#add-code-coverage-reporting)
- [Adding badges to your README](#adding-badges-to-your-readme)
- [Adding ES6 Support](#adding-es6-support)
- [Adding ES6 Support to Tests using Mocha and Babel](#adding-es6-support-to-tests-using-mocha-and-babel)
- [Limit Built Branches on Travis](#limit-built-branches-on-travis)
- [Add a browser build to an npm module](#add-a-browser-build-to-an-npm-module)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

---

## Introduction to How to Write an Open Source JavaScript Library

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-introduction)
- micro libraries
  - pros
    - small enough to reason about the code
    - easy to test as there is less code
    - easy to reuse via `npm install`
  - cons
    - managing dependencies as there could be too many

- objective of the course / learn to
  - create a Git repository
  - host it on GitHub
  - create the library
  - publish it to npm
  - create a full test suite for it using
    - karma
    - mocha
    - chai
  - set up continuous integration
  - add ES6 or ES2015 using Babel
  - integrate webpack
  - distribute this as both browser and node consumable

## Setting up GitHub

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-setting-up-github)
- create a GitHub account, if you don't have one
- sign in to your account and create a new repository
- follow the instructions displayed after creating the repository, to push your code to that repository
- that's all! GitHub setup is complete

## Configuring npm and creating a package.json

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-configuring-npm-and-creating-a-package-json)
- install node if not already installed
- configure npm locally to make publishing a little easier, for example
  - `$ npm set init-author-name "Sarbbottam Bandyopadhyay"`
  - `$ npm set init-author-url "https://sarbbottam.github.io/"`
  - `$ npm set init-author-email "sarbbottam@gmail.com"`
  - `$ npm set init-license "MIT"`
- these will be used as defaults values during `npm init`
- verify configuration
  - `$ cat ~/.npmrc`
- refer https://docs.npmjs.com/misc/config for more information
- recommended setting
  - `save-exact` property, it tells `npm` to use the exact version of the packages, rather than a version range, while saving dependency to package.json.
  - it safeguards when semver is not followed properly or there's a mistake in a release.
- create a npm account, if you don't have one at [npmjs.com](https://www.npmjs.com/)
- `$ npm add-user`, to add your account
  - enter username, password, and email when prompted
- it will create your `auth token` and add it to `~/.npmrc`
- `$ npm init` will prompt for desired information and create `package.json` at the end
- `$ npm init --yes` will create a `package.json`, with the defaults, with out prompting

## Creating the library and adding dependencies

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-creating-the-library-and-adding-dependencies)
- create the `main` file
- install required dependencies
  - use `-S` or `--save` to save it as `dependency` at `package.json`
  - use `-D` or `--save-dev` to save it as `devDependency` at `package.json`
- create the functionality

## Pushing to GitHub

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-pushing-to-github)
- create a `.gitignore` at the `root` of the project, to list all the ignored files and directories
- `$ git add <file-name>` to stage the changes
  - alternatively [`$ git add --all`](https://github.com/sarbbottam/conf-files/blob/master/git-confs/gitconfig#L20) to stage all the changes
- `$ git commit` to commit the changes
- `$ git push origin <repo-name>` to push the changes to GitHub(`origin`)
  - `$ git remote -v` will display all the available `remote` and their corresponding `url`

## Publishing to npm

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-publishing-to-npm)
- `$ npm add-user`, if you have not already
- add `package.json/files` to [whitelist the set of files to be published](https://docs.npmjs.com/files/package.json#files)
- you can also add `.npmignore` file to ignore files/directories, that might fall under from whitelist
- `$ npm version <patch|minor|major>`, if you have already published to npm
  - `patch` for bug fix
  - `minor` for new feature
  - `major` for breaking changes
- [`npm pack`](https://docs.npmjs.com/cli/pack) or [`npm link`](https://docs.npmjs.com/cli/link) to validate the module to be publish
- `$ npm publish`
- verify the released package at `npm.im/<package-name>`

## Releasing a version to GitHub

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-releasing-a-version-to-github)
- add a version tag to git repository
  - to associate the version released at npm to the corresponding code
- `tag` in git point to a specific commit
- `$ git tag <version>`
  - <version> released to npm
- `$ git push --tags`
  - GitHub will consider the tag as release and will make it available under `releases` tab
- draft new release
  - fill out the release form with the tag version

## Releasing a new version to npm

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-releasing-a-new-version-to-npm)
- make the update
- update the version `$ npm version <patch|minor|major>`
  - `patch` for bug fix
  - `minor` for new feature
  - `major` for breaking changes
- commit the changes
- tag to the commit.
- push that to GitHub
- push the tags to GitHub
- `$ npm publish`

## Publishing a beta version

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-publishing-a-beta-version)
- make changes
- manually update the package version in `package.json`
  - add `-beta.0` to the end of the version
- `$ git checkout -b <branch-name>` for the beta version
- `$ git tag <packge-version-beta.0>`
- `$ git push origin <branch-name>`
- `$ git push --tags`
- `$ npm publish --tag beta`
- verify published versions
  - `$ npm info`

## Setting up Unit Testing with Mocha and Chai

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-setting-up-unit-testing-with-mocha-and-chai)
- `$ npm i -D mocha chai`, to install and add them to `devDependencies`
- create a test file
  - `require(chai)`
  - `require` the file to be tested

  ```js
  var expect = require('chai').expect;
  var functionality = required('./path/to/index.js');

  describe('functionality', function() {
    it('should validate the functionality', function() {
      expect(true).to.be.true;
    });
  });
  ```
- update `package.json/script.test`
  - `{"scripts": { "test": "mocha path/to/test/file" } }`
  - add `-w` to watch for changes
- `$ npm test` to run test

## Unit Testing with Mocha and Chai

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-unit-testing-with-mocha-and-chai)
- use the `global` `describe` function and `it` function to describe the tests and what they should do
- validate functionalities by assertions using `expect`

## Automating Releases with semantic-release

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-automating-releases-with-semantic-release)
- `semantic-release` automates the releasing and avoid redundant manual steps.
- `$ npm i -g semantic-release-cli` to install `semantic-release-cli` globally
- `$ semantic-release setup`
  - it will take you through the interactive prompt
  - it will create a `travis.yml` if the CI system chosen, is travis.
  - it will update `package.json/script` w.r.t `release`
  - it will remove the `version` from `package.json`
    - as the version will be determied dynamically from the commit messages
- this `script` will be executed on `success`
- update `travis.yml` to run tests prior releasing
- update the `package.json/version` to `0.0.0-sematically-released`, to avoid `npm` warning

## Writing conventional commits with commitizen

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-writing-conventional-commits-with-commitizen)
- commit message [convention](https://github.com/angular/angular.js/blob/master/CONTRIBUTING.md#-git-commit-guidelines)
- `$ npm i -D commitizen cz-conventional-changelog`
  - install `commitizen` globally  or add `./node_modules/bin` to system `PATH` [to use `git cz` instead of `git commit`](https://github.com/commitizen/cz-cli#installing-the-command-line-tool)
  - alternatively you could use `npm scripts`, `{"scripts": { "commit": "git-cz" } }`
- [configure `commitizen`](https://github.com/commitizen/cz-cli#making-your-repo-commitizen-friendly) via `{config": { "commitizen": { "path": "cz-conventional-changelog" } } }`

## Committing a new feature with commitizen

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-committing-a-new-feature-with-commitizen)
- make changes to `source` and `test`
- use `commitizen` to commit with conventional message
- push the changes to GitHub

## Automatically Releasing with TravisCI

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-automatically-releasing-with-travisci)
- travis build is automatically setup by semantic-release
  - if for some reason it is not enabled, manually sync github repo and enable travis build
- if the build is successful travis will run `semantic-release`
- depending on the commit messages `semantic-release` would
  - push a new version to npm
  - push a new tag and release to github along with change history since the previous version

## Automatically running tests before commits with ghooks

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-automatically-running-tests-before-commits-with-ghooks)
- `$ npm i -D ghooks` to install and add it to `package.json/devDependencies`
- configure `ghooks` via the `{"config": {"ghooks": { "hook-name": "command-to-execute" } } }`

## Adding code coverage recording with Istanbul

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-adding-code-coverage-recording-with-istanbul)
- `$ npm i istanbul`
- update `package.json/script.test`
  - `{"scripts": { "test": "istanbul cover -x test-file-name-pattern _mocha -- path/to/test/file -R spec" } }`
- `$ npm test` will run the test and generate coverage information at `coverage/` folder
- add `coverage` to `.gitignore` file

## Adding code coverage checking

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-adding-code-coverage-checking)
- create a script called `check-coverage` to verify coverage for statements, branches, functions, and lines.
  - `{"scripts": { "check-coverage": "istanbul check-coverage --statement 100 --branches 100 --function 100 --lines 100" } }`
- add `npm run check-coverage` to `travis/script`
- you can also add it to `git hooks`
  - `{"config": {"ghooks": { "pre-commit": "npm test && npm run check-coverage" } } }`

## Add code coverage reporting

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-add-code-coverage-reporting)
- signup for [codecov.io](https://codecov.io/)
- `$ npm i codecov.io -D`
- create a script called `report-coverage` to report coverage to [codecov.io](https://codecov.io/).
  - `{"scripts": { "report-coverage": cat ./coverage/lcov.info | codecov" } }`
- add `npm run report-coverage` to `travis/after_success`
- after successful build the reports will be pushed to [codecov.io/github/<user-name/organization-name>/<repo-name>](https://codecov.io/)
- check out [codecov browser extension](https://www.youtube.com/watch?v=d6wJKODB8_g&feature=youtu.be)

## Adding badges to your README

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-adding-badges-to-your-readme)
- check out [shields.io](http://shields.io/)
- add badges via `[![alt text](badge-url)](link to the service)`
  - for example: `[![build](https://img.shields.io/travis/<user-name>/<repo-name>.svg)](https://travis-ci.org/<user-name/organization-name>/<repo-name>)`
- you can also pass the `style` query param to customize the style of the badge
  - `https://img.shields.io/...svg?style=flat-square`

## Adding ES6 Support

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-adding-es6-support)
- need a transpiler to write code with latest JavaScript specs
- use [babel](http://babeljs.io/)
- `$ npm i -D babel-cli` to install and add it to `package.json/devDependencies`
- create a script called `build` to transpile ES6/ES2015 code to ES5
  - `{"scripts": { "build": "babel --out-dir dist src" } }`
  - you can use `-d` instead of `--out-dir`
  - use `--copy-files` to copy dependencies
    - `{"scripts": { "build": "babel --copy-files --out-dir dist src" } }`
  - checkout [babel/setup/cli](http://babeljs.io/docs/setup/#cli) for further details
- add a script called `prebuild` to clean the `dist` directory prior building
  - `{"scripts": { "prebuild": "rimraf dist" } }`
  - `$ npm i -D rimraf` to install and add it to `package.json/devDependencies`
- install desired babel presets/plugin and add it to `package.json/devDependencies`
  - `$ npm i -D babel-preset-es2015`
  - `$ npm i -D babel-preset-stage-2`
  - checkout [babel/pluglin](http://babeljs.io/docs/plugins/) for further details
- create babel config
  - either in a `.babelrc` file or in `package.json/babel`
  - `.babelrc` - `$ echo '{ "presets": ["es2015", "stage-2] }' > .babelrc`
  - `package.json` - `{ "babel" : { "presets": ["es2015", "stage-2] } }`
- `$ npm run build` will create the transpiled code in `dist` folder
- update `package.json/main` to refer `dist`
- add `npm run build` to `travis.yml/script`
- add `dist/` to `.gitignore`

## Adding ES6 Support to Tests using Mocha and Babel

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-adding-es6-support-to-tests-using-mocha-and-babel)
- `npm i -D babel-register` to install and add it to `package.json/devDependencies`
- pass `babel-rgister` as the compiler to `mocha` and update `package.json/scripts.test`
  - `{"scripts": { "test": "mocha path/to/test/file --compilers js:babel-register" } }``
- `$ npm i -d nyc` to install and add it to `package.json/devDependencies`
- add a script called `cover`
  - `{"scripts": { "cover": "nyc npm test" } }``
- update `ghook` and `travis/script` run `npm run cover` instead of `npm test`
- replace `istanbul` with `nyc` at `package.json/scripts.check-coverage`
  - `{"scripts": { "check-coverage": "nyc check-coverage --statement 100 --branches 100 --function 100 --lines 100" } }`
- add [`.nyc_output`](https://github.com/bcoe/nyc/issues/197) to `.gitignore`

## Limit Built Branches on Travis

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-limit-built-branches-on-travis)
- add `branches` to  `travis.yml`
```yml
branches
- only
  - master
```
- `only` for whitelisting and `exclude` for blacklisting
- `branch-name` (`master`) could also be a `regex`
- travis will continue to build for pull requests

## Add a browser build to an npm module

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-add-a-browser-build-to-an-npm-module)
- `$ npm i -D webpack`
- create `webpack.config.babel.js`
  - for example, checkout [getting-started/#config-file](http://webpack.github.io/docs/tutorials/getting-started/#config-file)
- add `libraryTarget: 'umd'` to `output`
- add `library: <library-name>` to `output`
- add `devtool: 'source-map'` to main config
- install [`loaders`](https://webpack.github.io/docs/using-loaders.html)
  - `$ npm i -D bable-loader`
 - rename the current `package.json/script.build` to `package.json/script.build:main`
 - add `"build:umd": "webpack --output-filename <output-file-name>.umd.js"` to `package.json/script`
 - add `"build:umd:min": "webpack --output-filename <output-file-name>.umd.min.js" -p` to `package.json/script`
   - `-p` for production build, minify the code
- `"build": "build:main && build:umd && build:umd:min"` to `package.json/script`
- alternatively
  - `$ npm i -D npm-run-all`
  - `"build": "npm-run-all build:*"` to `package.json/script`
- update `readme` to point to `https://npmcdn.com/<package-name>@<version>/path/to/umd/file`
