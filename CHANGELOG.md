## 1.1.0 - 2026-11-13

Minor:
* Modernize packaging: move build metadata from setup.py into pyproject.toml, remove setup.py; require Python >=3.10 - [#58](https://github.com/octodns/octodns-easydns/pull/58)

Patch:
* Page through all records when populating zones with more than 1000 records - [#64](https://github.com/octodns/octodns-easydns/pull/64)

## 1.0.1 - 2026-04-03

Patch:
* Use new [changelet](https://github.com/octodns/changelet) tooling - [#42](https://github.com/octodns/octodns-easydns/pull/42)

## v1.0.0 - 2025-05-03 - Long overdue 1.0

* Address pending octoDNS 2.x deprecations, require minimum of 1.5.x

## v0.0.1 - 2022-01-07 - Moving

#### Nothworthy Changes

* Initial extraction of EasyDnsProvider from octoDNS core
* Renamed classes from all caps DNS to Dns, permanent shim in place for EasyDNSProvider

#### Stuff

Nothing
