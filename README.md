Night Zookeeper House Rules
===

## Introduction

This is CoffeeScript. Whitespace is significant (that means that you will have to indent your code properly) and you're about to read that although the language allows you to omit braces, parentheses and semi-colons everywhere, it's not always what's the most readable.

This coding style is derived from working with CoffeeScript for a while but also what both the JavaScript and CoffeeScript community recommends (you can have a look in the references). Two rules:

- This is the coding style. Stick to it. *All* the time.
- Don't do anything stupid and everything will be fine.

Now, as a rule of thumb, clarity and consistency should be your first concern. If you want don't know what to do, imagine you're writing an essay: follow the English syntax rules and one idea per paragraph. Also, we're based in the UK, write in British English.

## Naming

Be descriptive. It doesn't mean that you have to write sentences as function or variable names, but that you shouldn't try to 'optimise' by using small variable names. One letter variables are allowed as iterators (and in loop comprehensions if necessary).

[EXAMPLE]

Use **PascalCase** for required libraries, modules and classes  
Use **camelCase** for everything else (functions, methods, properties, variables, etc.)  
Use **ALL_CAPS** for constants  
Prefix jQuery variables with `$`  
Prefix private/internal things with `_` if there's no `internals` object

[EXAMPLE]

Use the plural form for arrays and collections and the singular form for single items

[EXAMPLE]

Use vocabulary like is, has, set and get where possible.  
Starting Boolean variables with is is recommended.  
Avoid private words such as `default, private, delete, continue, new, arguments`

[EXAMPLE]

Avoid numbers in variable names except for third party modules (S3 etc.)

Replace `this` with `@` everywhere

[EXAMPLE]

## General

There is no hard limit on line length, however there's a soft limit of **120** characters and it's always best if it's under **80**.  

Use double quotes for user messages and string interpolations (no one like to escape a stray single quote). Don't use `+` for variables use `#{…}`.  
Use single quotes for identifiers, keys, and basically everything where it would make no sense to have string interpolation in the future.  
Use triple quotes for multiline strings (e.g. templates).

[EXAMPLE]

Never begin a line with an operator

[EXAMPLE]

if method chaining and too long/ugly to fit on one line, use leading . and one statement per line.

[EXAMPLE]

Do not extend native objects like Array, Object, etc.

Use `delete` only to remove a property from an object, otherwise set the property to null (not undefined).

In classes, one line methods are allowed (no need for a new line). They should be grouped together at the top of the class after the static methods. They should still be separated by a blank line.

Accessor functions for properties are allowed but not required. If you start needing to access lots of properties or need accessors, maybe think about a Backbone Model.

[EXAMPLE OF CLASS WITH ACCESSOR]

CoffeeScript has fancy boolean values, however `true` and `false` are still preferred. If it makes more semantic sense, using `yes` and `no` is tolerated (as long as it is consistent everywhere the variable is referenced). Avoid `no` and `off` (these are functions in jQuery!).

[EXAMPLE WITH IS VARIABLES]

Don't assign to return.

[EXAMPLE]

## Whitespace

Use hard tabs for indentation (representing 4 or 2 spaces depending on your preference).

Two rules borrowed from the English syntax:

- There is _always_ a space after a comma, **never** before. No leading commas, always at the end of the previous line (except for an array of objects where the comma can stand on its own with the correct indentation)
- There is _always_ a space after a colon, **never** before

[EXAMPLE]

No spaces immediately inside parentheses or array brackets.  
Spaces immediately inside inline objects (braces).  
One space after the argument list of a function declaration

You can align the content of a single assignment but be wary of CoffeeScript's meaningful indentation. Don't try to align assignments visually. It never works and it's a pain to maintain.

[EXAMPLE]

There is a blank line at the end of a file. No trailing whitespace otherwise.
There is _always_ a blank line before a block statement (if, for, functions, etc.) unless immediately nested.
There is _always_ a blank line between function/methods declarations except inline.

As a rule of thumb, avoid cramped/packed blocks of instructions, they are hard to decipher and navigate. GIVE THE CODE SOME DAMN SPACE.

[EXAMPLE]

There is _always_ spaces around operators such as `*, +, -, /, <=, >=,  =, is, isnt, and, or, in, not, etc.`. There is _always_ a space after a keyword.
In rare cases, for example calculating indexes in between brackets, space around the mathematical operators can be omitted.

[EXAMPLE]

## Conditions

The CoffeeScript keywords replacing ==, != etc. are preferred over their JavaScript equivalent. A non exhaustive list: `or, and, not, is, isnt`.
When checking existence of a value in an array, use `in`.

Conditions don't need to be surrounded by parentheses. You should still use parentheses to outline groups in your condition.  
For single conditions leading to a one liner, prefer the postfixed notation

[EXAMPLE]

CoffeeScript introduces `unless`. Never use it with an `else`, it doesn't read well at all. Unless should be avoided most of the time, except if it's postfixed for a negative condition.

Avoid ternary expression and break them down on multiple lines. Check that it can't be solved by a comparative assignment first. Ternaries are tolerated in strings interpolations, object assignment, inline function.

[EXAMPLE]

Use `?=` when you want to set a value to a variable only if it's `undefined` or `null`.  
Use `or=` when you want to change the value of a variable if it returns `false`.  
In both these cases, it will force the left side variable to be declared before the statement can be made.

Use `?` to check for existence (not `null` and not `undefined`), a simple `if` is enough to check for falsy/thruthy values.

As a reminder:

- `Objects` evaluate to `true`
- `Undefined` evaluates to `false`
- `Null` evaluates to `false`
- `Booleans` evaluate to the value of the boolean
- `Numbers` evaluate to `false` if `+0, -0, or NaN`, otherwise `true`
- `Strings` evaluate to `false` if an empty string `''`, otherwise `true`

[EXAMPLE]

Multiline if/else have to use indentation.

[EXAMPLE]

Multiline conditions are encouraged if they become too long/hard to read

[EXAMPLE]

A word of warning on chained comparison. They look cleaner but are a little less easy to read as the first comparison is inverted. It's probably best to use them solely to compare numbers, however other uses are tolerated as long as they are understandable.

[EXAMPLE]

## Objects & Arrays

Array and objects work by reference. Be careful how you assign and copy them.  
To get a copy of an array you can use `slice()`. If you want a more versatile function call for both arrays and objects, use `_.clone()`.

Don't use braces except for empty objects and inline objects (they should be removed if the object is the only argument of a function). Use indentation to show structure of the object/array.  
Objects should only be inlined if they are short, improve readability and are unlikely to change often.

[EXAMPLE]

Remove commas when using objects or array with significant whitespace, except when necessary (e.g. array of objects).  
Use the literal array notation (`[]`) and if the array is multiline place the opening bracket on the line as the variable assignment.

[EXAMPLE]

For ranges, make sure you know the difference between `..` and `…` as `..` is inclusive and `…` is exclusive. Stick to `..` or have notes explaining why the choice (for instance allows to not have an ugly `-1` to get the right index).

[EXAMPLE]

Use the safe navigation operator `?` when accessing a property or chain of properties that may be null. If you have to use it too many times, think about what you're doing!

[EXAMPLE]

Use subscript notation (`[]`) when accessing object properties with a variable. Otherwise use the dot notation.

[EXAMPLE]

CoffeeScript has a powerful array comprehension syntax, make the most of it:

- Use a postfixed `for`
- Use the keyword `when` if you need to filter an array based on one or multiple conditions.
- Surround the whole thing with parentheses when assigning the result to an array

[EXAMPLE]

Use `of` to iterate over key/values of an object
Use `in` to loop over an array

[EXAMPLE]


## Functions

Don't declare functions in a block (if, while, for, etc.).  
Use parentheses for all function calls except when there's a callback or object as last argument.  
When declaring a function, if it doesn't take arguments don't use the parentheses.

[EXAMPLE]

_Always_ use the return keyword, unless it's a single line statement (namely a inline/lambda function).
If a function doesn't return anything, use an empty return statement. That's because in CoffeeScript the return is implicit and for instance if the last statement of your function is a loop, it will do some extra work to be able to return something.  
If you want to enable method chaining, return `@`.

[EXAMPLE]

Callbacks should follow the node convention:

- The callback is the last argument of the function and is called `callback`
- `err` is the first argument and is null (or a falsy value) when the callback is successful
- The second argument is more flexible in its naming (data, res or more semantically depending on what you're expecting in return e.g a list of things can use a plural), can be omitted if err isn't null

Conditional/optional callbacks and functions should be call with the safe navigation operator `?`.

[EXAMPLE]

Changing context is easy in CoffeeScript with the fat arrow (`=>`). Don't abuse it, think about why you have to save the context (generally because of a nested function or a jQuery DOM callback).


## Comments

_This is borrowed almost straight from Hapi's style guide_

Line comment:

- Provides narrative for the following single code line (or single statement broken for readability)
- One line of comment only
- One blank line before and none after the comment line

Segment comment:

- Provides narrative for the following code section (one or more lines of code, with or without line breaks)
- One or more lines of comments
- One blank line before and one after comments block

Note:

- Explains the behaviour of a single code statement (can be broken into multiple lines)
- Used to document unexpected behaviour or non-standard practice
- Appears immediately at the end of the line (or statement) it describes, following whitespace to separate it from code block

FIXME/TODO:

- Leave a more global note the current code situation (alternative solution, etc.)
- FIXME if it's a hack that deserve a refactor in the near future
- TODO if there's a way to improve the current code. Can be used to keep a TODO list of the things to do on a class for instance



## Tips

_These are a collection of best practices collected from different sources. It's encouraged behaviour and most of the time cannot be enforced. It's something to keep in mind when you're structuring the code._

Always check underscore before doing anything stupid (omit, pluck, map...)  
If you have to assign multiple values to an object, check if you can use `_.extend` or `_.defaults`.

[EXAMPLE]

Prefer objects over list of arguments in constructor (think Backbone).
You can use destructed assignment in the constructor to improve readability.  
	`{@name, @age, @height} = options` or `{@name, @age, @height}`
Alternatively, `_.defaults` or `_.extend` can be used.

[EXAMPLE]

Prefer objects to argument list in general (events, function, etc.) to allow adding more properties later and for better readability. If there's a lot of arguments, think about how it would look if it was an object instead. For example a series of flags, when written in the function call they are meaningless and object properties makes it clearer what flags you are using.

[EXAMPLE]

Be careful with CoffeeScript's local variable auto assignment. It's 98% of the time what you want to do and avoids global variables (that should not be used except when attaching the whole app to the global namespace for instance). However, if you are referencing an already existing global variable, it will overwrite it instead of creating a local var with the same name.

Only use `typeof` only to check if something is `undefined` (or maybe, a function). Prefer the existential operator `?`. You can use `_.isArray, _.isObject, etc.` methods if needed.

When building some HTML to be inserted, build a DOM fragment/string and do a single insert instead of doing multiple inserts. A common approach is to build each string in an array, then use `join('')` to concatenate it. Combined with loop comprehensions this can be pretty powerful.

[EXAMPLE]

Prefer `Number()` over `parseInt()`, unless you know what you're doing (and specify a radix).  
Use `Boolean()` to convert a `Number` value to `Boolean`.

Prefer `text()` over `html()` when injecting content in the DOM. If you have to use `html()` make **EXTRA** sure that you are escaping the user provided values (you can use `_.escape`).

Don't embed JavaScript unless you really have to (an external lib/snippet that you REALLY can't convert).

iI you have to use a `switch`, think twice and provide why.

Learn the difference between `++i` and `i++`, more often than not you will want to use `++i`.

Setters can be one-liners by putting the @ variable in the argument list.

[EXAMPLE]


## Git, GitHub & File Organisation

Use branches and branch often.  
The `master` branch has the code that can go in production any time. 
Branch from `master` when you add a feature/fix then push your branch to GitHub. Submit a pull request when ready.  
If you need to build on top of a feature, branch off that feature branch if it hasn't been merged. Don't merge your own pull request, wait for review.  
Branch names should start with `feature/` if it's a feature, `fix/` if it's a fix and `refactor/` if it's a refactor.

If the code is made to be deployed check in the `npm_module` folder and similar folders containing libraries. It keeps the dependencies on a manageable level and the server doesn't have to download them and risk a different version.

Regardless, use `npm shrinkwrap` to get a more accurate package.json.

Use semantic versioning for the tags and version numbers:

- MAJOR version when you make incompatible API changes,
- MINOR version when you add functionality in a backwards-compatible manner, and
- PATCH version when you make backwards-compatible bug fixes.

Use **snake-case** for file names. Make directories to group files instead of appending things to the file names. If the file contains a class, name it after the class name.


# References

## Javascript

- [https://github.com/styleguide/javascript](https://github.com/styleguide/javascript)
- [https://github.com/stevekwan/best-practices/blob/master/javascript/best-practices.md](https://github.com/stevekwan/best-practices/blob/master/javascript/best-practices.md)
- [https://github.com/Seravo/js-winning-style](https://github.com/Seravo/js-winning-style)
- [https://github.com/airbnb/javascript](https://github.com/airbnb/javascript)
- [https://github.com/rwaldron/idiomatic.js](https://github.com/rwaldron/idiomatic.js)
- [https://github.com/spumko/hapi/blob/master/docs/Style.md](https://github.com/spumko/hapi/blob/master/docs/Style.md)
- [https://npmjs.org/doc/coding-style.html](https://npmjs.org/doc/coding-style.html)

## CoffeeScript

- [https://github.com/polarmobile/coffeescript-style-guide](https://github.com/polarmobile/coffeescript-style-guide) and [https://github.com/mbarkhau/coffeescript-style-guide](https://github.com/mbarkhau/coffeescript-style-guide)
- [https://gist.github.com/jashkenas/1005723](https://gist.github.com/jashkenas/1005723)
- [http://arcturo.github.io/library/coffeescript/04_idioms.html](http://arcturo.github.io/library/coffeescript/04_idioms.html)
- [https://github.com/jashkenas/coffee-script/issues/425](https://github.com/jashkenas/coffee-script/issues/425)
- [http://coffeescript.org](http://coffeescript.org)
- [https://github.com/bevry/community/wiki/Coding-Standards](https://github.com/bevry/community/wiki/Coding-Standards)

## Git

- [http://www.futurealoof.com/posts/nodemodules-in-git.html](http://www.futurealoof.com/posts/nodemodules-in-git.html)
- [http://scottchacon.com/2011/08/31/github-flow.html](http://scottchacon.com/2011/08/31/github-flow.html)
