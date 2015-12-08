# ScuttleZanetti
CLI and node.js library to access and remove stop words

# Examples
## CLI
```
npm install -g scuttlezanetti
> echo "this is a test" | scuttlezanetti
test
> echo "this is a test" | scuttlezanetti --stop-words test,is
this a
> echo "this,is,a,test" | scuttlezanetti --tokenize-pattern '\W+'
test
```

### Preserve lines in file
```
while read CMD; do
    echo "$CMD" | scuttlezanetti && echo
done < "./input" > output
```

## Node.js
> npm install scuttlezanetti

```javascript
var ScuttleZanetti = require( 'scuttlezanetti' ).api;
var stopWords = require( 'scuttlezanetti' ).stopWords;

var sz =  = new ScuttleZanetti( {
  stopWords: stopWords,   //default
  tokenizePattern: undefined, //default
  tokenizeMethod: function( s ) {
    return s.replace(/[^\w\s-]/, "").split( " " );
  } //default
} );

sz.tokenize( "this is a test" ); //[ 'this', 'is', 'a', 'test' ]
sz.removeStopWords( "this is a test" ); //'test'
```
