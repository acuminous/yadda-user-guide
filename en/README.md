# Yadda User Guide

Yadda brings _true_ BDD to JavaScript test frameworks such as [Jasmine](http://pivotal.github.io/jasmine/), [Mocha](http://visionmedia.github.io/mocha/), [QUnit](http://qunitjs.com), [Nodeunit](https://github.com/caolan/nodeunit), [WebDriverJs](http://code.google.com/p/selenium/wiki/WebDriverJs) and [CasperJS](http://casperjs.org). By _true_ BDD we mean that the ordinary language (e.g. English) steps are mapped to code, as opposed to simply decorating it. This is important because just like comments, the decorative steps such as those used by
[Jasmine](http://pivotal.github.com/jasmine), [Mocha](http://visionmedia.github.io/mocha) and [Vows](http://vowsjs.org) can fall out of date and are a form of duplication.

Yadda's BDD implementation is like [Cucumber's](http://cukes.info/) in that it maps the ordinary language steps to code. Not only are the steps less likely to go stale, but they also provide a valuable abstraction layer and encourage re-use. You could of course just use [CucumberJS](https://github.com/cucumber/cucumber-js), but we find Yadda less invasive and prefer its flexible syntax to Gherkin's. Yadda's conflict resolution is smarter too.
