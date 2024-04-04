# Tokenvm Subnet using the Avalanche HyperSDK

The `tokenvm` using the Avalanche HyperSDK allows anyone create any asset, mint more of their asset, modify the metadata of their asset (if they reveal some info), and burn their asset. Additionally, there is an embedded on-chain exchange that allows anyone to create orders and fill (partial) orders of anyone else. To make this example easy to play with, the tokenvm also bundles a powerful CLI tool and serves RPC requests for trades out of an in-memory order book it maintains by syncing blocks.

## Demo Videos

https://www.loom.com/share/355e74efcf144b40bb5db905b6910657?sid=ecd5a5d0-a7f1-4069-bd26-6d3fca54185f

### Completing the consts.go

`consts/consts.go`

```go
const (
	// TODO: choose a human-readable part for your hyperchain
	HRP = "Hugo Waters Capitals Chain"
	// TODO: choose a name for your hyperchain
	Name = "Hugo Waters"
	// TODO: choose a token symbol
	Symbol = "HWC"
)

```

### Registering the Missing Actions

`registry/registry.go`

```go
// TODO: register action: actions.CreateAsset
consts.ActionRegistry.Register(&actions.CreateAsset{}, actions.UnmarshalCreateAsset, false),

// TODO: register action: actions.MintAsset
consts.ActionRegistry.Register(&actions.MintAsset{}, actions.UnmarshalMintAsset, false),
```

### Successfully Setup my subnet

- Step 1

```bash

MODE="run-single" ./scripts/run.sh

```

- Step 2

```bash

./scripts/build.sh

```

- Step 3

```bash

./build/token-cli key import demo.pk

```

- Step 4

```bash

./build/token-cli chain import-anr

```

## Interacting with the Subnet

### Creating Asset

```bash

./build/token-cli action create-asset

```

### Minting Tokens

```bash

./build/token-cli action mint-asset

```

### Checking Balance

```bash

./build/token-cli key balance

```
## Author

Ugo Mars
[@metacraftersio](https://github.com/UgoMars)

## License

This project is licensed under the MIT License - see the LICENSE.md file for details.
