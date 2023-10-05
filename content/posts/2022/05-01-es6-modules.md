---
title: ES6 Modules
description: ES6 Modules
date: 2022-05-01
tags:
  - es6
  - javascript
  - modules
---

ES6 or ECMAScript 2015 is the 6th version of the ECMAScript programming language. ECMAScript is the standardization of Javascript which was released in 2015 and subsequently renamed as ECMAScript 2015. ECMAScript and Javascript are both different in nature.

**ECMAScript vs Javascript** 

ECMAScript: It is the specification defined in ECMA-262 for creating a general-purpose scripting language. In simple terms, it is a standardization for creating a scripting language. It was introduced by Ecma International and is basically an implementation with which we learn how to create a scripting language. 

Javascript: A general-purpose scripting language that conforms to the ECMAScript specification.It is basically an implementation that tells us how to use a scripting language. [001](https://www.geeksforgeeks.org/introduction-to-es6/#:~:text=ES6%20or%20ECMAScript%202015%20is,ECMAScript%20vs%20Javascript)

## Strict Mode

## export

In CommonJS, you export values by exposing them on `module.exports`. As seen in the snippet below, you could expose anything from a value type to an object, an array, or a function.

```sh
module.exports = 1
module.exports = NaN
module.exports = 'foo'
module.exports = { foo: 'bar' }
module.exports = ['foo', 'bar']
module.exports = function foo () {}
```
ES6 modules are files that `export` an API – just like CommonJS modules. Declarations in ES6 modules are scoped to that module, just like with CommonJS. That means that any variables declared inside a module aren’t available to other modules unless they’re explicitly exported as part of the module’s API (and then imported in the module that wants to access them).

### Export a default binding

You can mimic the CommonJS code we just saw by changing `module.exports` = into `export default`.

```sh
export default 1
export default NaN
export default 'foo'
export default { foo: 'bar' }
export default ['foo', 'bar']
export default function foo () {}
```

Contrary to CommonJS, `export` statements can only be placed at the top level in ES6 modules – even if the method they’re in would be immediately invoked when loading the module. Presumably, this limitation exists to make it easier for compilers to interpret ES6 modules, but it’s also a good limitation to have as there aren’t that many good reasons to dynamically define and expose an API based on method calls.

```sh
function foo () {
  export default 'bar' // SyntaxError
}
foo()
```

There isn’t just `export default`, you can also use *named exports*.

### Named Exports

In CommonJS you don’t even have to assign an object to `module.exports` first. You could just tack properties onto it. It’s still a single binding being exported – *whatever properties* the `module.exports` object ends up holding.

```sh
module.exports.foo = 'bar'
module.exports.baz = 'ponyfoo'
```

We can replicate the above in ES6 modules by using the named exports syntax. Instead of assigning to `module.exports` like with CommonJS, in ES6 you can declare bindings you want to `export`. Note that the code below cannot be refactored to extract the variable declarations into standalone statements and then just `export foo`, as that’d be a syntax error. Here again, we see how ES6 modules favor static analysis by being rigid in how the declarative module system API works.

```sh
export var foo = 'bar'
export var baz = 'ponyfoo'
```

It’s important to keep in mind that we are exporting *bindings*.

### Bindings, Not Values

An important point to make is that ES6 modules export bindings, not values or references. That means that a `foo` variable you export would be bound into the `foo` variable on the module, and its value would be subject to changes made to `foo`. I’d advise against changing the public interface of a module after it has initially loaded, though.

If you had an `./a` module like the one found below, the `foo` export would be bound to `'bar'` for 500ms and then change into `'baz'`.

```sh
export var foo = 'bar'
setTimeout(() => foo = 'baz', 500)
```

Besides a “default” binding and individual bindings, you could also export lists of bindings.

### Best Practices and `export`

Having the ability to define named exports, exporting a list with aliases and whatnot, and also exposing a *“default”* `export` will mostly introduce confusion, and *for the most part* I’d encourage you to use `export default` – and to do that at the end of your module files. You could just call your API object `api` or name it after the module itself.

```sh
var api = {
  foo: 'bar',
  baz: 'ponyfoo'
}
export default api
```

**One**, the exported interface of a module becomes immediately obvious. Instead of having to crawl around the module and put the pieces together to figure out the API, you just scroll to the end. Having a clearly defined place where your API is exported also makes it easier to reason about the methods and properties your modules export.

**Two**, you don’t introduce confusion as to whether `export default` or a named export – or a list of named exports *(or a list of named exports with aliases...)* – should be used in any given module. There’s a guideline now – just use `export default` everywhere and be done with it.

**Three**, consistency. In the CommonJS world *it is usual* for us to export a single method from a module, and that’s it. Doing so with named exports is impossible as you’d effectively be exposing an object with the method in it, unless you were using the `as default` decorator in the `export` list flavor. The `export default` approach is more versatile because it allows you to `export` just one thing.

**Four**, – and this is really a reduction of points made earlier – the `export default` statement at the bottom of a module makes it immediately obvious what the exported API is, what its methods are, and generally easy for the module’s consumer to `import` its API. When paired with the convention of **always using `export default` and always doing it at the end of your modules**, you’ll note using the ES6 module system to be painless.

Now that we’ve covered the `export` API and its caveats, let’s jump over to `import` statements.


### `import`

These statements are the counterpart of `export`, and they can be used to load a module from another one – first and foremost. The way modules are loaded is *implementation-specific*, and at the moment no browsers implement module loading. This way you can write spec-compliant ES6 code today while smart people figure out how to deal with module loading in browsers. Transpilers like Babel are able to concatenate modules with the aid of a module system like CommonJS. That means `import` statements in Babel follow *mostly* the same semantics as `require` statements in CommonJS.

Let’s take `lodash` as an example for a minute. The following statement simply loads the Lodash module from our module. It doesn’t create any variables, though. It **will execute** any code in the top level of the `lodash` module, though.

```sh
import 'lodash'
```

Before going into importing bindings, let’s also make a note of the fact that `import` statements, – much like with `export` – are only allowed in the top level of your module definitions. This can help transpilers implement their module loading capabilities, as well as help other static analysis tools parse your codebase.

### Importing Default Exports

In CommonJS you’d `import` something using a `require` statement, like so.

```sh
var _ = require('lodash')
```

To import the default exported binding from an ES6 module, you just have to pick a name for it. The syntax is a bit different than declaring a variable because you’re **importing a binding**, and also to make it easier on static analysis tools.

```sh
import _ from 'lodash'
```

You could also import named exports and alias them.

## Importing Named Exports

The syntax here is very similar to the one we just used for default exports, you just add some braces and pick any named exports you want. Note that this syntax is similar to the destructuring assignment syntax, but also bit different.

```sh
import {map, reduce} from 'lodash'
```

Another way in which it differs from destructuring is that you could use aliases to rename imported bindings. You can mix and match aliased and non-aliased named exports as you see fit.

```sh
import {cloneDeep as clone, map} from 'lodash'
```

You can also mix and match named exports and the default export. If you want it inside the brackets you’ll have to use the default name, which you can alias; or you could also just mix the default import side-by-side with the named imports list.

```sh
import {default, map} from 'lodash'
import {default as _, map} from 'lodash'
import _, {map} from 'lodash'
```

Lastly, there’s the `import *` flavor.

### `import` All The Things

You could also import the namespace object for a module. Instead of importing the named exports or the default value, it imports all the things. Note that the `import *` syntax must be followed by an alias where all the bindings will be placed. If there was a default export, it’ll be placed in `alias.default`.

```sh
import * as _ from 'lodash'
```

That’s about it!

[ES6 Modules in Depth](https://ponyfoo.com/articles/es6-modules-in-depth)

more

[Exploring ES6 Modules](https://exploringjs.com/es6/ch_modules.html#ch_modules)
