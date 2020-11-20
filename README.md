# Hardhat ABI Exporter

Export Solidity contract ABIs on compilation via Hardhat.

Versions of this plugin prior to `2.0.0` were released as `buidler-abi-exporter`.

## Installation

```bash
yarn add --dev hardhat-abi-exporter
```

## Usage

Load plugin in Hardhat config:

```javascript
require('hardhat-abi-exporter');
```

Add configuration under the `abiExporter` key:

| option | description | default |
|-|-|-|
| `path` | path(s) to ABI export directory (relative to Hardhat root or external dir if `allowExternalDir` is true) | `'./abi'` or `['./abi', './abi2']`
| `clear` | whether to delete old files in `path` on  | `false` |
| `flat` | whether to flatten output directory (may cause name collisions) | `false` |
| `only` | `Array` of contracts to include (case sensitive), defaults to all contracts if `length` is 0 | `[]` |
| `except` | `Array` of contracts to exclude (case sensitive) | `[]` |
| `allowExternalDir` | whether to allow writing to dirs outside of working dir | `false` |

```javascript
abiExporter: {
  path: './data/abi', // or ['./data/abi', './data2/abi2']
  clear: true,
  flat: true,
  allowExternalDir: true,
  only: ['ERC20'],
}
```

The `path` directory will be created if it does not exist.

The `clear` option is set to `false` by default because it represents a destructive action, but should be set to `true` in most cases.

ABIs files are saved in the format `[CONTRACT_NAME].json`.
