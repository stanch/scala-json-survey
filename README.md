# JSON survey

This project aims to provide a comprehensive summary of JSON libraries in Scala:

1. [Basic features](#basic-features): the essentials for working with JSON, mapping it to/from case classes, etc.
2. [Library support](#library-support): which base libraries are supported by various projects in the wild.

## Basic features

| Base library | Automatic codec derivation | Immutable manipulation | JSON Schema |
| --- | --- | --- | --- |
| [Play JSON][1] | [included, macro-based][2]; [shapeless-based][3] | [lens-based][4] | [yes][5] |

## Library support

| Library | Play JSON |
| --- | --- |
| Akka HTTP | [yes][6] |
| JWT | [yes][7] |


[1]: https://www.playframework.com/documentation/2.5.x/ScalaJson
[2]: https://www.playframework.com/documentation/2.5.x/ScalaJsonAutomated
[3]: https://github.com/julienrf/play-json-derived-codecs
[4]: https://github.com/mandubian/play-json-zipper
[5]: https://github.com/eclipsesource/play-json-schema-validator
[6]: https://github.com/hseeberger/akka-http-json
[7]: https://github.com/pauldijou/jwt-scala
