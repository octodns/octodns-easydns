# Developer Agent Guide for octoDNS easyDNS Provider

This repository contains the easyDNS provider for octoDNS. It enables planning, syncing, and applying DNS record states directly to the easyDNS REST API.

> [!IMPORTANT]
> **Core Workflow and Guidelines**
>
> All agents working on this repository must read and follow the general instructions and workflow guidelines defined in the core octoDNS `AGENTS.md` file.
> - **Local check**: Look for the file at `../octodns/AGENTS.md`.
> - **Remote check**: If the local file is not available, fetch it from GitHub: [octoDNS Core AGENTS.md](https://github.com/octodns/octodns/raw/refs/heads/main/AGENTS.md).
>
> You must align your code structure, style, pull request guidelines, and overall development workflows with the instructions specified there.

## Repository & Module Information

### Key Components

- **Provider Class**: [EasyDnsProvider](file:///home/ross/octodns/octodns-easydns/octodns_easydns/__init__.py#L373-L475) (defined in [octodns_easydns/__init__.py](file:///home/ross/octodns/octodns-easydns/octodns_easydns/__init__.py)). This is the primary provider mapping record models.
- **Client Class**: [EasyDnsClient](file:///home/ross/octodns/octodns-easydns/octodns_easydns/__init__.py#L40-L370) manages HTTP communication with easyDNS REST APIs.
- **Authentication**: Authenticates using HTTP Basic Auth configured via `token` and `api_key` base64 encoding.

### Key Workflows & Features

1. **Supported Record Types**: `A`, `AAAA`, `ALIAS`, `CAA`, `CNAME`, `MX`, `NS`, `PTR`, `SRV`, `TXT`.
2. **Domain Provisioning Settings**: easyDNS requires configuring domain settings for additions:
   - `currency` (defaults to `CAD`): Payment currency.
   - `portfolio` (defaults to `myport`): The portfolio name to assign domains.
   - `domain_create_sleep`: Provisioning pause timer in seconds to wait for easyDNS to propagate domain registration internally before applying record changes.
3. **Sandbox Environment**: Supports setting `sandbox=True` during initialization to route API requests to `https://sandbox.rest.easydns.net` instead of production `https://rest.easydns.net`.
4. **Dynamic Routing**: Not supported (`SUPPORTS_DYNAMIC=False`, `SUPPORTS_GEO=False`).
5. **Dynamic Subnets**: Not supported (`SUPPORTS_DYNAMIC_SUBNETS=False`).
6. **Pool Value Status**: Not supported (`SUPPORTS_POOL_VALUE_STATUS=False`).

## Development & Testing

- **Setup Script**: Run `./script/bootstrap` to create a virtual environment, install dependencies (including `black`, `isort`, `pyflakes`, and `pytest`), and configure pre-commit hooks.
- **Test Suite**: Run unit tests using `pytest` via `./script/test` (or `pytest tests/`). Test files are located in [tests/](file:///home/ross/octodns/octodns-easydns/tests).
- **Code Coverage**: Verify code coverage using `./script/coverage`.

## Key Constraints & Behaviors

- **Python Version**: Targets Python `>=3.9`.
- **Formatting**: Code formatting is enforced via `black` (version `>=26.0.0,<27.0.0`) and `isort`.
