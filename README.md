javascript-idents
=================

javascript-idents walks a JavaScript AST and collects all Identifier AST nodes. It relies on Marijn
Haverbeke's [acorn.js](http://marijnhaverbeke.nl/acorn/) for AST walking, and it should be
compatible with any [SpiderMonkey Parser
API](https://developer.mozilla.org/en-US/docs/SpiderMonkey/Parser_API)-compliant JavaScript AST.

It is intended for use in node.js but can be adapted to work in other JavaScript environments.


Example
-------

The following example prints the name of each Identifier AST node to the console.

```javascript
var acorn = require('acorn'), idents = require('javascript-idents');

var src = 'var c = a.b[d]; function f(w, x, y) { return z; }';
var astNode = acorn.parse(src);
idents.inspect(astNode, function(ident) {
  console.log('Ident:', ident.name);
});

// output:
// Ident: c
// Ident: a
// Ident: b
// Ident: d
// Ident: f
// Ident: w
// Ident: x
// Ident: y
// Ident: z
```


Running tests
=============

Run `npm test`.


Contributors
============

* Quinn Slack <sqs@sourcegraph.com>
