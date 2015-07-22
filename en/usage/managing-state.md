# Managing State
It's common to setup data in one step that you want to refer to in a subsequent one. An easy way to do this is by adding a property in a library, but when you need to share state between steps in separate libraries you can use Yadda's contexts.

```js
var library = Yadda.localisation.English.library()
    .given('a user called $name', function(name) {
        this.ctx[name] = new User(name);
    })
    .when('$name logs in', function(name) {
        var user = this.ctx[name];
        user.login();
    })

Yadda.createInstance(library, { ctx: {} }).run(steps);

```
