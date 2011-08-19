!SLIDE
# Your JavaScript
![Browserify!](687474703a2f2f737562737461636b2e6e65742f696d616765732f62726f777365726966792f62726f777365726966792e706e67.png)

!SLIDE bullets

# Why?

* require()
* packaging
* npm

!SLIDE

# require()

## In the olden days:

    @@@ sh
    $ cat lib/A.js  > build/application.js
    $ cat lib/B.js >> build/application.js
    $ cat lib/C.js >> build/application.js

!SLIDE

# node.js + CommonJS

    @@@ javascript
    var Aircraft = require('vehicles/Aircraft');

    var Dirigible = function() {};
    Dirigible.prototype = new Aircraft();

    // ...

    module.exports = Dirigible;

!SLIDE

# Easier testing

    @@@ javascript
    var Dirigible = require('vehicles/Aircraft/Dirigible');
    var vows = require('vows'),
        assert = require('assert');

    vows.describe('Dirigible').addBatch({
      '#speed': {
        'returns speed in m/s': function() { /* ... */ }
      }
    }).export(module);

!SLIDE

# require() - Easier testing

    @@@ sh
    $ vows test/vehicles/Aircraft/Dirigible-test.js
    X Errored
        in #speed
        in Dirigible
        in test/vehicles/Aircraft/Dirigible-test.jsâ

!SLIDE

# Packaging

    @@@ sh
    $ npm install browserify
    $ ./node_modules/.bin/browserify \
        -o build/application.js -e lib/MyLib.js

!SLIDE

# npm

    @@@ sh
    $ npm install JSONPath
    $ npm install jquery-browserify

!SLIDE

# npm

    @@@ sh
    $ ./node_modules/.bin/browserify \
        -r JSONPath -r jquery-browserify \
        -o build/application.js -e lib/MyLib.js

!SLIDE bullets

# More

* https://github.com/substack/node-browserify
* https://github.com/brighterplanet/careplane
* http://numbers.brighterplanet.com/

!SLIDE bullets

# Me

* @dkastner
* Brighter Planet (http://brighterplanet.com)
