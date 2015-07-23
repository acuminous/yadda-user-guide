## Examples

Yadda includes several [examples](https://github.com/acuminous/yadda/tree/master/examples), which demonstrate all the key features available and how to integrate Yadda with the common of test frameworks. To run the examples...

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
