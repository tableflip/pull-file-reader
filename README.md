# filereader-pull-stream

Given an HTML5 File object (from e.g. HTML5 drag and drops), turn it into a pull stream source.

# install

Use it with npm & [browserify](/substack/node-browserify)

```bash
npm install filereader-pull-stream
```

# example

```js
var drop = require('drag-and-drop-files')
var pull = require('pull-stream')
var fileReaderPullStream = require('filereader-pull-stream')

drop(document.body, function (files) {
  var first = files[0]
  pull(
    fileReaderStream(first),
    pull.collect(function (err, buffs) {
      var contents = Buffer.concat(buffs)
      // contents is the contents of the entire file
    })
  )
})

```

# usage

```js
var fileReaderPullStream = require('filereader-pull-stream')
var source = fileReaderPullStream(file, [options])
```

`fileReaderPullStream` is a [pull stream](https://github.com/pull-stream/pull-stream) [source](https://github.com/pull-stream/pull-stream#source-aka-readable).

`options`:

* `chunkSize` - default `1024 * 1024` (1MB) - How many bytes will be read at a time
* `offset` - default `0` - Where in the file to start reading

# run the tests

```
npm install
npm test
```

then open your browser to the address provided, open your JS console, and drag and drop files onto the page until the test suite passes/fails
