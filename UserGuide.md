# User Guide

TODO document user guide intro

## Import

To import this module, please type:

```swift
import SwiftyZeroMQ
```

## Low-level API

Low-level API is available once you import this module, ZeroMQ C++ API is
usually prefixed by `zmq_`. For example, to print library version, please
type:

```swift
var major: Int32 = 0
var minor: Int32 = 0
var patch: Int32 = 0
zmq_version(&major, &minor, &patch)
print("ZeroMQ library version is \(major).\(minor).\(patch)")
```

For more information about the ZeroMQ low level API, please consult
[ZeroMQ 4.1 API](http://api.zeromq.org/4-1:_start).

## High level API

High-level API is available once you import this module under the `SwiftyZeroMQ`
virtual namespace (i.e. struct). The following section describe the high-level
API.

### Version

To get the ZeroMQ library version as a tuple, please use `SwiftyZeroMQ.version`.
If you need a version string, please use `SwiftyZeroMQ.versionString`. The
following examples show typical usage:

```swift
// Version as a tuple
let (major, minor, patch) = SwiftyZeroMQ.version
print("ZeroMQ library version is \(major).\(minor).\(patch)")

// Version as a string
let versionString = SwiftyZeroMQ.versionString
print("ZeroMQ library version is \(versionString)")
```

### Capability

Use `SwiftyZero.has` to check whether the ZeroMQ capability (or feature) is
enabled or not. The list of capabilities (or features) that can be checked:
- `.ipc`    - the library supports the `ipc://` protocol
- `.pgm`    - the library supports the `pgm://` protocol
- `.tipc`   - the library supports the `tipc://` protocol
- `.norm`   - the library supports the `norm://` protocol
- `.curve`  - the library supports the [`CURVE`](http://curvezmq.org) security
  mechanism
- `.gssapi` - the library supports the GSSAPI security mechanism

The following examples show typical usage:

```swift
if SwiftyZeroMQ.has(.ipc) {
  print "The library supports the ipc:// protocol"
}

if SwiftyZeroMQ.has(.curve) {
  print("The library supports the CURVE security mechanism")
}
```