# Changelog

## v2.0.0

* **Breaking change**: File logging is now disabled by default, it can be enabled by setting
  `dendrite_logging_file: true`.

* Bump Dendrite version to v0.5.1

* Enable the following MSC's by default: msc2836 (Threading), msc2946 (Spaces Summary)

## v1.1.0

* Add config option `dendrite_enabled_mscs` to enable MSC's supported by Dendrite. Defaults to an empty list.

* Bump Dendrite version to v0.3.5

## v1.0.0 - 2020-12-30

* Initial release
