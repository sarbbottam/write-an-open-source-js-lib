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

- [Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-setting-up-github)

## Configuring npm and creating a package.json

- [Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-configuring-npm-and-creating-a-package-json)

## Creating the library and adding dependencies

- [Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-creating-the-library-and-adding-dependencies)

## Pushing to GitHub

- [Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-pushing-to-github)

## Publishing to npm

- [Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-publishing-to-npm)

## Releasing a version to GitHub

- [Direct link to the video tutorial](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-releasing-a-version-to-github)

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

