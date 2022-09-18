# Changelog

## v2.6.0

* Bump Dendrite to v0.9.8

## v2.5.0

* Bump Dendrite to v0.9.6

## v2.4.0

* Bump Dendrite to v0.8.9

* Add config option `dendrite_report_stats_enabled` which by default is `false`. Controls
  reporting server statistics to matrix.org.

* Fix missing persisting of JetStream path

## v2.3.0

* Bump Dendrite to v0.8.1

* Allow configuring presence

## v2.2.0

* Bump Dendrite to v0.6.4

## v2.1.0

* Bump Dendrite to v0.6.2

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
