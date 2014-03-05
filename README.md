# node-pg-pure-alias

A `pg` alias for [pg.js][pg.js].

## Why?
The fantastic [pg](https://github.com/brianc/node-postgres) package
bundles both native and pure JavaScript bindings for PostgreSQL. This
means you have to compile the native bindings, whether you want them or
not.

To compensate, [pg.js][pg.js] bundles only the JavaScript bindings. This is
great until you use a library like [Knex][knex], which is hard-coded to import a
library called `pg`.

So this package aliases `pg` to `pg.js` to trick Knex into importing the right
package.

## Usage

node-pg exports whatever version of pg.js you depend on in your
`package.json`.

If you forget to depend on pg.js yourself, node-pg will blow up when you try to
`require` it.

#### package.json
```json
{
  "dependencies": {
    "pg": "git+https://github.com/WhoopInc/node-pg-pure-alias.git#1.0.0",
    "pg.js": "x.x.x",
    "..."
  }
}
```

#### *.js
```javascript
var pg = require("pg");
// `pg` is now vx.x.x of the pg.js package. No native bindings! Shh!
```

[pg.js]: https://github.com/brianc/node-postgres-pure
[knex]: https://github.com/tgriesser/knex
[peer-dep]: http://blog.nodejs.org/2013/02/07/peer-dependencies/

## It's not in NPM!
We're shadowing the official NPM 'pg' package!

If you're concerned about depending on this GitHub repository,
fork this repository and host the package under your own namespace.
