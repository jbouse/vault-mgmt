# Vault Management Toolkit 🧰

A collection of CLI tools for managing, comparing, migrating, and rolling out HashiCorp Vault clusters, with support for OIDC authentication and Kubernetes rollouts.

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](LICENSE)
[![Python Versions](https://img.shields.io/badge/python-3.9%2B-blue.svg)](https://www.python.org/downloads/)
[![GitHub Issues](https://img.shields.io/github/issues/ugns/vault-mgmt.svg)](https://github.com/ugns/vault-mgmt/issues)

---

## Features

- **Secure OIDC Authentication** for Vault clusters
- **Detailed Secret Comparison** between Vault instances
- **Full RAFT Snapshot Migration** with selective overrides
- **Kubernetes Rollout Management** for Vault clusters
- **CLI entry point**: `vault-mgmt`

---

## Installation

### Using pip (recommended)

```bash
pip install .
# or for development
pip install -e .
```

---

## CLI Usage

The toolkit provides a unified CLI:

```bash
vault-mgmt [command] [options]
```

---

## Example Workflows

### Compare Vaults

```bash
vault-mgmt compare --source-vault-addr ... --destination-vault-addr ... --output-file differences.csv
```

### Sync Vaults with Overrides

```bash
vault-mgmt sync --source-vault-addr ... --destination-vault-addr ... --override-secrets differences.csv
```

### Kubernetes Rollout

```bash
vault-mgmt rollout vault-namespace --vault-addr ... --kube-context ...
```

---

## Development

- **Testing:**
  ```bash
  pytest
  ```
- **Linting:**
  ```bash
  ruff check .
  ```
- **Tox:**
  ```bash
  tox
  ```

---

## Dependencies

| Package            | Version    | Description                                    |
|--------------------|-----------|------------------------------------------------|
| `hvac`             | 2.1.0     | Python client for HashiCorp Vault API          |
| `kubernetes`       | 29.0.0    | Python client for Kubernetes API               |
| `requests`         | 2.32.3    | Elegant HTTP library (dependency of `hvac`)    |
| `tqdm`             | 4.66.4    | Progress bar for loops and iterables           |
| `certifi`          | 2024.6.2  | Mozilla's root certificates for SSL/TLS        |
| `charset-normalizer`| 3.3.2    | Character set/encoding detection               |
| `idna`             | 3.7       | Internationalized Domain Names in Applications |
| `urllib3`          | 2.2.1     | HTTP client for Python (dependency of requests)|

---

## Project Structure

- `vault_mgmt/` — Main package with CLI and submodules:
  - `cli.py` — CLI entry point
  - `compare.py` — Vault comparison logic
  - `sync.py` — Vault migration/sync logic
  - `rollout.py` — Kubernetes rollout logic
  - `manager.py` — Shared management utilities

---

## Links

- [GitHub Repository](https://github.com/ugns/vault-mgmt)
- [Issue Tracker](https://github.com/ugns/vault-mgmt/issues)

---

## License

GPL-3.0-only. See [LICENSE](LICENSE).