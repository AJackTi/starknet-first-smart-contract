# Starknet First Smart Contract Example

This repository provides a simple example of deploying and interacting with a smart contract on StarkNet. It serves as a beginner-friendly introduction to the basics of contract development, deployment, and interaction using Cairo and StarkNet tools.

## Installation

Install scarb and starkli before start the project. I'm using scarb version [2.6.0](https://crates.io/crates/cairo-lang-compiler/2.6.0) and starkli version [0.3.4](https://github.com/xJonathanLEI/starkli/releases/tag/v0.3.4)

```bash
scarb --version
```

```bash
starkli --version
```

## Usage

```bash
git clone git@github.com:AJackTi/starknet-first-smart-contract.git
cd starknet-first-smart-contract
```

1. Build the project:

```bash
scarb build
```

2. Create keystore:

```bash
starkli signer keystore new ./test-wallet
```

3. Create account:

```bash
starkli account oz init ./test-account --keystore ./test-wallet
```

4. Deploy account:

```bash
starkli account deploy ./test-account --keystore ./test-wallet
```

5. Declare contract:

```bash
starkli declare ./target/dev/starknet-first-smart-contract_simple_storage.contract_class.json --account ./test-account --keystore ./test-wallet
```

---

WARNING: you're using neither --rpc (STARKNET_RPC) nor --network (STARKNET_NETWORK). The sepolia network is used by default. See https://book.starkli.rs/providers for more details.
Enter keystore password:
Sierra compiler version not specified. Attempting to automatically decide version to use...
Network detected: sepolia. Using the default compiler version for this network: 2.7.1. Use the --compiler-version flag to choose a different version.
Declaring Cairo 1 class: 0x06f3c64c631e6309fb3309bad49da9ec293f230131f66524280ad920fb07337c
Compiling Sierra class to CASM with compiler version 2.7.1...
CASM class hash: 0x06ac0a5558ac6f3352384715845b0233831a07c68b7f060786007c9b00f11ff4
Contract declaration transaction: 0x00d8a8627fcba30ccbf561643134f3e5c765d0782b71a17bc4b92152d4b356fa
Class hash declared:
0x06f3c64c631e6309fb3309bad49da9ec293f230131f66524280ad920fb07337c

---

6. Deploy contract:

```bash
starkli deploy 0x06f3c64c631e6309fb3309bad49da9ec293f230131f66524280ad920fb07337c --account ./test-account --keystore ./test-wallet
```

## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License

[MIT](https://choosealicense.com/licenses/mit/)
