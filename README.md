# JSON survey

This project aims to provide a comprehensive summary of JSON libraries in Scala:

1. [Basic features](#basic-features): the essentials for working with JSON, mapping it to/from case classes, etc.
2. [Library support](#library-support): which base libraries are supported by various projects in the wild.
3. [Links and resources](#links-and-resources): further reading.

## Basic features

In this section we explore the essentials for working with JSON:

* Simple JSON construction — an easy way to construct the JSON tree.
  * *DSL* — something like `("name" -> "joe") ~ ("age" -> 35)` (json4s);
  * *interpolator* — something like `json"""{name: "joe", age: 35}"""` (jsonquote).
* Codecs — how data (mostly case classes) is converted to JSON.
  * *typeclass-based* — a more flexible approach, checked at compile-time;
  * *reflection-based* — somewhat non-idiomatic, not checked at compile-time.
* Automatic codec derivation — whether manual labor is required to convert case classes and sealed traits into JSON.
  * *macro-based* — fast, but typically somewhat ad-hoc and lacking support for sealed traits, multiple `apply` methods in the companions, etc;
  * *shapeless-based* — might take more time to compile, but provides robust support for arbitrary case classes and sealed traits.
* Immutable manipulation — an easy way to manipulate JSON, modify, remove fields, etc. (You can learn more about lenses and zippers from [my talk](https://github.com/stanch/unzimm)!)
  * *zipper-based* — something like `(cursor --\ "outerKey" --\ "innerkey2").withFocus(_.withString(_ + "!"))` (argonaut);
  * *lens-based* — something like `json.updateAs[String](__ \ "outerKey" \ "innerkey2", _ + "!")` (play-json-zipper — contrary to what the name suggests).
* Diff & patch — diffing and patching JSON along the lines of [RFC 6902](https://tools.ietf.org/html/rfc6902).
* JSON Schema — validing JSON against a schema along the lines of [RFC ???](http://json-schema.org/).

| Base library | Simple JSON construction | Codecs | Automatic codec derivation | Immutable manipulation | Diff & patch | JSON Schema |
| --- | --- | --- | --- | --- | --- | --- |
| [Argonaut][10] | [included DSL][29] | [typeclass-based][16] | [included, macro-based][10]; [shapeless-based][14] | [included, zipper-based][11] | [yes][24] | ? |
| [Circe][20] | ? | [typeclass-based][20] | [included, shapeless-based][20] | [included, zipper-based][20] | [no][25] | ? |
| [json4s][21] | [included DSL][28] | [reflection-based][22] | [included, reflection-based][22] | [included, path-based][23] | [included][26] | ? |
| [Play JSON][1] | [included][30]; [interpolator-based][31] | [typeclass-based][17] | [included, macro-based][2]; [shapeless-based][3] | [lens-based][4] | [yes][27] | [yes][5] |
| [Spray JSON][12] | [interpolator-based][31] | [typeclass-based][12] | [included, reflection-based][12]; [shapeless-based][13] | [lens-based][15] | [yes][27] | ? |

## Library support

This section outlines the support for the above base libraries in the wild.

| Project/topic | Argonaut | Circe | json4s | Play JSON | Spray JSON |
| --- | --- | --- | --- | --- | --- |
| Akka HTTP | [yes][6] | [yes][6] | [yes][6] | [yes][6] | [yes][6] |
| JWT | ? | [yes][7] | [yes][7] | [yes][7] | [yes][7] |
| Slick Postgres | [yes][8] | [yes][8] | [yes][8] | [yes][8] | [yes][8] |
| GeoJSON | [yes][19] | ? | ? | [yes][9] | [yes][18] |

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
[21]: https://github.com/json4s/json4s
[22]: https://github.com/json4s/json4s#serialization
[23]: https://github.com/json4s/json4s#xpath--hofs
[24]: https://github.com/stacycurl/delta/blob/master/argonaut/src/test/scala/sjc/delta/argonaut/RFC6902JsonSpec.scala
[25]: https://github.com/travisbrown/circe/issues/281
[26]: https://github.com/json4s/json4s#merging--diffing
[27]: https://github.com/gnieh/diffson
[28]: https://github.com/json4s/json4s#dsl-rules
[29]: http://argonaut.io/doc/json/
[30]: https://www.playframework.com/documentation/2.5.x/ScalaJson#Converting-to-a-JsValue
[31]: https://github.com/maffoo/jsonquote
