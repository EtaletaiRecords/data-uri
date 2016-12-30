# DataURI
[![Language](https://img.shields.io/badge/Swift-3-brightgreen.svg)](http://swift.org)
[![Build Status](https://travis-ci.org/nodes-vapor/data-uri.svg?branch=master)](https://travis-ci.org/nodes-vapor/data-uri)
[![codecov](https://codecov.io/gh/nodes-vapor/data-uri/branch/master/graph/badge.svg)](https://codecov.io/gh/nodes-vapor/data-uri)
[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/nodes-vapor/data-uri/master/LICENSE)

A pure Swift parser for Data URIs.

## Integration
Update your `Package.swift` file.
```swift
.Package(url: "https://github.com/nodes-vapor/data-uri.git", majorVersion: 0)
```

## Getting started 🚀
There are two options for decoding a Data URI. The first is using the `String` extension and the second is by using the `DataURIParser` directly.

### The `String` method
This method is by far the easiest to use. All you need to do is call `.dataURIDecoded() throws -> (data: Bytes, type: String)` on any Data URI encoded `String`.

```swift
import Core //just for `Bytes.string`
import DataURI

let uri = "data:,Hello%2C%20World!"
let (data, type) = try uri.dataURIDecoded()
print(data.string) // "Hello, World!"
print(type) // "text/plain;charset=US-ASCII"
```

### The `DataURIParser` method
Using the parser is a bit more involved as it returns all of its results as `Bytes`.

```swift
import Core //just for `Bytes.string`
import DataURI

let uri = "data:text/html,%3Ch1%3EHello%2C%20World!%3C%2Fh1%3E"
let (data, type, metadata) = try DataURIParser.parse(uri: uri)
print(data.string) // "<h1>Hello, World!</h1>"
print(type.string) // "text/html"
print(metadata == nil) // "true"
```


## 🏆 Credits
This package is developed and maintained by the Vapor team at [Nodes](https://www.nodes.dk).

## 📄 License
This package is open-sourced software licensed under the [MIT license](http://opensource.org/licenses/MIT)