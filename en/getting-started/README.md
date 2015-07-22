# Getting Started

If you intend to use Yadda for functional web testing then we recommend reviewing the following frameworks which build on top of Yadda and make this easier.

* [moonraker](https://github.com/LateRoomsGroup/moonraker) by LateRooms - An out of the box solution for bdd web testing using the page object pattern.
* [cucumber-boilerplate](https://github.com/webdriverio/cucumber-boilerplate) - boilerplate project for an easy and powerful setup of Yadda and [WebdriverIO](http://webdriver.io/) with predefined common Webdriver steps
* [mimik](https://www.npmjs.com/package/mimik) - Mimik is a behavior-driven testing framework and UI automation platform.
* [massah](https://www.npmjs.com/package/massah) - Making BDD style automated browser testing with node.js very simple.
* [y2nw](https://www.npmjs.com/package/y2nw) - Yadda to [NightWatch](http://nightwatchjs.org) integration

## Installation

Yadda can be used in node or browser environments

### Node.js

    npm i --save-dev yadda

### Browser

    <script src="https://rawgit.com/acuminous/yadda/master/dist/yadda-<VERSION>.js" />

## Tutorial

If you're new to Yadda we suggest following the [tutorial](../tutorial).

## Examples

There are also several [examples](https://github.com/acuminous/yadda/tree/master/examples), which can be run sequentially...

```
git clone https://github.com/acuminous/yadda.git
cd yadda
npm install
npm link
npm run examples
```

or individually...

```
git clone https://github.com/acuminous/yadda.git
cd yadda
npm install
npm link
cd examples/<desired-example-folder>
npm install
npm test
```

#### Caveats
* The Zombie example doesn't install on windows, and is currently skipped in other environments (the tests started failing, so the site under test has probably changed.)
* The webdriver example may fail depending on how google detects your locale.
* Your operating system must support ```npm link```.

#### More Examples
* There's a great example of how to use Yadda on large scale projects [here](https://github.com/adlnet/xAPI_LRS_Test/tree/master/src). Thanks very much to [brianjmiller](https://github.com/brianjmiller) for sharing.
* There is a [pull request](https://github.com/acuminous/yadda/pull/99) showing how to get yadda working with [Appium](http://appium.io/). It didn't work out of the box so hasn't been pulled.
* Issues [#58](https://github.com/acuminous/yadda/issues/58) and [#148](https://github.com/acuminous/yadda/issues/148) discuss integrating Yadda with [Karma](http://karma-runner.github.io/0.13/index.html)


