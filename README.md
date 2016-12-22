# DataURI
[![Language](https://img.shields.io/badge/Swift-3-brightgreen.svg)](http://swift.org)
[![Build Status](https://travis-ci.org/nodes-vapor/DataURI.svg?branch=master)](https://travis-ci.org/nodes-vapor/DataURI)
[![codecov](https://codecov.io/gh/nodes-vapor/DataURI/branch/master/graph/badge.svg)](https://codecov.io/gh/nodes-vapor/DataURI)
[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/nodes-vapor/DataURI/master/LICENSE)

A pure Swift parser for Data URIs.

## Integration
Update your `Package.swift` file.
```swift
.Package(url: "https://github.com/nodes-vapor/DataURI.git", majorVersion: 0)
```

## Getting started 🚀
There are two options for decoding a Data URI. The first is using the `String` extension and the second is by using the `DataURIParser` directly.

### The `String` method
This method is by far the easiest to use. All you need to do is call `.dataURIDecoded() throws -> (type: String, data: Bytes)` on any Data URI encoded `String`.

```swift
let uri = "data:,Hello%2C%20World!"
let (type, data) = try uri.dataURIDecoded()
print(type) // "text/plain;charset=US-ASCII"
print(data.string) // "Hello, World!"
```

### The `DataURIParser` method
Using the parser is a bit more involved as it returns all of its results as `Bytes`.

```swift
let uri = "data:text/html,%3Ch1%3EHello%2C%20World!%3C%2Fh1%3E"
let (type, metadata, data) = try DataURIParser.parse(uri: uri)
print(type.string) // "text/html"
print(metadata == nil) // "true"
print(data.string) // "<h1>Hello, World!</h1>"
```


## 🏆 Credits
This package is developed and maintained by the Vapor team at [Nodes](https://www.nodes.dk).

## 📄 License
This package is open-sourced software licensed under the [MIT license](http://opensource.org/licenses/MIT)