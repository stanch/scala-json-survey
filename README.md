# JSON survey

This project aims to provide a comprehensive summary of JSON libraries in Scala:

1. [Basic features](#basic-features): the essentials for working with JSON, mapping it to/from case classes, etc.
2. [Library support](#library-support): which base libraries are supported by various projects in the wild.
3. [Links and resources](#links-and-resources): further reading.

## Basic features

| Base library | Custom codecs | Automatic codec derivation | Immutable manipulation | JSON Schema |
| --- | --- | --- | --- | --- |
| [Argonaut][10] | [typeclass-based][16] | [shapeless-based][14] | [included, zipper-based][11] | ? |
| [Circe][20] | [typeclass-based][20] | [included, shapeless-based][20] | [included, zipper-based][20] | ? |
| [Play JSON][1] | [typeclass-based][17] | [included, macro-based][2]; [shapeless-based][3] | [lens-based][4] | [yes][5] |
| [Spray JSON][12] | [typeclass-based][12] | [included, reflection-based][12]; [shapeless-based][13] | [lens-based][15] | ? |

## Library support

| Library | Argonaut | Circe | Play JSON | Spray JSON |
| --- | --- | --- | --- | --- |
| Akka HTTP | [yes][6] | [yes][6] | [yes][6] | [yes][6]
| JWT | ? | [yes][7] | [yes][7] | [yes][7] |
| Slick Postgres | [yes][8] | [yes][8] | [yes][8] | [yes][8] |
| GeoJSON | [yes][19] | ? | [yes][9] | [yes][18] |

## Links and resources

* [A quick tour of JSON libraries in Scala](http://manuel.bernhardt.io/2015/11/06/a-quick-tour-of-json-libraries-in-scala/)
* [Awesome Scala, JSON section](https://github.com/lauris/awesome-scala#json)


[1]: https://www.playframework.com/documentation/2.5.x/ScalaJson
[2]: https://www.playframework.com/documentation/2.5.x/ScalaJsonAutomated
[3]: https://github.com/julienrf/play-json-derived-codecs
[4]: https://github.com/mandubian/play-json-zipper
[5]: https://github.com/eclipsesource/play-json-schema-validator
[6]: https://github.com/hseeberger/akka-http-json
[7]: https://github.com/pauldijou/jwt-scala
[8]: https://github.com/tminglei/slick-pg
[9]: https://github.com/jroper/play-geojson
[10]: http://argonaut.io/
[11]: http://argonaut.io/doc/zipper/
[12]: https://github.com/spray/spray-json
[13]: https://github.com/fommil/spray-json-shapeless
[14]: https://github.com/alexarchambault/argonaut-shapeless
[15]: https://github.com/jrudolph/json-lenses
[16]: http://argonaut.io/doc/codec/
[17]: https://www.playframework.com/documentation/2.5.x/ScalaJsonCombinators
[18]: https://github.com/MonsantoCo/mwundo
[19]: https://github.com/shiplog/argonaut-geojson
[20]: https://github.com/travisbrown/circe
