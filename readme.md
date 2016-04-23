Companion for [How to Write an Open Source JavaScript Library](https://egghead.io/series/how-to-write-an-open-source-javascript-library)
---

Watch the series at [egghead.io](https://egghead.io/series/how-to-write-an-open-source-javascript-library), if you haven't already.

The purpose of this document is to serve as a ready reckoner of the  [How to Write an Open Source JavaScript Library](https://egghead.io/series/how-to-write-an-open-source-javascript-library)

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

- learn
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
- create a GitHub account if you don't have one
- sign in to your account and create a new repository
- follow the instructions displayed on creating the repository to push your code to that repository
- that's all GitHub setup is complete

## Configuring npm and creating a package.json

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-configuring-npm-and-creating-a-package-json)
- install node if not already installed
- configure npm locally to make publishing a little easier, for example
  - `$ npm set init-author-name "Sarbbottam Bandyopadhyay"
  - `$ npm set init-author-url "https://sarbbottam.github.io/"`
  - `$ npm set init-author-email "sarbbottam@gmail.com"`
  - `$ npm set init-license "MIT"`
- this will be used as default values during `npm init`
- verify configuartion
  - `$ cat ~/.npmrc`
- refer https://docs.npmjs.com/misc/config for more information
- recommended setting
  - save-exact property, it tells `npm` to use the exact version, rather than a version range, while saving dependency to package.json.
  - it safeguards when semver is not followed properly or there's a mistake in a release.
- create a npm account if you don't have one at [npmjs.com](https://www.npmjs.com/)
- `$ npm add-user` to add your account
  - enter username, password, and email when prompted
- it will create your `auth token` and add it to `~/.npmrc`
- `$ npm init` will prompt for desired information and create `package.json` at the end
- `$ npm init --yes` will create a `package.json` with out prompting with the defaults

## Creating the library and adding dependencies

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-creating-the-library-and-adding-dependencies)
- create the main file
- install required dependencies
  - use `-S` or `--save` to save it as `dependency` at `package.json`
  - use `-D` or `--save-dev` to save it as `devDependency` at `package.json`
- create the functionality

## Pushing to GitHub

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-pushing-to-github)
- create a .gitignore to list all the ignored files and directories
- `$ git add <file-name>` to stage the changes
- `$ git commit` to commit the changes
- `$ git push origin <repo-name>` to push the changes to GitHub(`origin`)
  - `$ git remote -v` will display all the available `remote` and its corresponding `url`

## Publishing to npm

[Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-publishing-to-npm)
- `$ npm add-user`, if you have not already
- `$ npm version <patch|minor|major>`, if you have already published to npm
  - `patch` for bug fix
  - `minor` for new feature
  - `major` for breaking changes
- `$ npm publish`

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

- [Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-releasing-a-new-version-to-npm)

## Publishing a beta version

- [Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-publishing-a-beta-version)

## Setting up Unit Testing with Mocha and Chai

- [Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-setting-up-unit-testing-with-mocha-and-chai)

## Unit Testing with Mocha and Chai

- [Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-unit-testing-with-mocha-and-chai)

## Automating Releases with semantic-release

- [Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-automating-releases-with-semantic-release)

## Writing conventional commits with commitizen

- [Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-writing-conventional-commits-with-commitizen)

## Committing a new feature with commitizen

- [Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-committing-a-new-feature-with-commitizen)

## Automatically Releasing with TravisCI

- [Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-automatically-releasing-with-travisci)

## Automatically running tests before commits with ghooks

- [Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-automatically-running-tests-before-commits-with-ghooks)

## Adding code coverage recording with Istanbul

- [Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-adding-code-coverage-recording-with-istanbul)

## Adding code coverage checking

- [Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-adding-code-coverage-checking)

## Add code coverage reporting

- [Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-add-code-coverage-reporting)

## Adding badges to your README

- [Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-adding-badges-to-your-readme)

## Adding ES6 Support

- [Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-adding-es6-support)

## Adding ES6 Support to Tests using Mocha and Babel

- [Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-adding-es6-support-to-tests-using-mocha-and-babel)

## Limit Built Branches on Travis

- [Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-limit-built-branches-on-travis)

## Add a browser build to an npm module

- [Direct link to the video tutorial](https://egghead.io/lessons/javascript-add-a-browser-build-to-an-npm-module)

