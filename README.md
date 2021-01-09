# stacks-dump

Dump information from `stacks-node` storage


## Prerequisites
- Node 14.x (older versions of nodejs. do no support the `import` syntax)
- yarn (use `npm install -g yarn`, the yarn command in the `cmdtest` package is not the right one)

## Installation

```
git clone git@github.com:psq/stacks-dump.git
cd stacks-dump
yarn
```

## Usage

Run the script using the current working directory for `stacks-node`, generally found in the `/tmp` folder unless specified via the config file.

### Default

```
node report /tmp/stacks-testnet-5c87e24790411516
```

### Options

#### Output stats as CSV
`-c` or `--csv` - display transactions in CSV format

```
node report -c /tmp/stacks-testnet-5c87e24790411516
```

#### Output block commit distances
`-d` or `--distances` - display block commit distance to latest btc block

```
node report -d /tmp/stacks-testnet-5c87e24790411516
```

#### End block
`-e BURN_BLOCK_HEIGHT` or `--end-block BURN_BLOCK_HEIGHT`
Rather than dump all blocks, will stop at BURN_BLOCK_HEIGHT - 1

#### Start block
`-s BURN_BLOCK_HEIGHT` or `--start-block BURN_BLOCK_HEIGHT`

Rather than dump all blocks, will start at BURN_BLOCK_HEIGHT


#### Show transactions
`-t` or `--tx-log` - display transactions for each block (if `stacks-node` is compiled with `--features tx_log`)

```
cargo build --workspace  --features tx_log --bin stacks-node

node report -t /tmp/stacks-testnet-5c87e24790411516
```

#### Dump `krypton` instead of `xenon`
`-k` or `--krypton` - the internal structure for `krypton` requires this option

```
node report -x /tmp/stacks-testnet-5c87e24790411516
```

#### Dump `xenon` instead of `krypton`, now the default if not included
`-x` or `--xenon` - the internal structure for `xenon` requires this option

```
node report -x /tmp/stacks-testnet-5c87e24790411516
```

#### List all known stacks-nodes
`-n` or `--nodes` - display list of nodes
```
node report -n /tmp/stacks-testnet-5c87e24790411516
```

## Support for older versions of Krypton
i.e. for version 24.0.x.x or 23.x.x.x, use `report-24.0.x.x` instead of `report`.  This will become obsolete very soon, but will be useful for some running the mining challenge on krypton

Note: one way to tell you need this version is if you get an error with `no such table: staging_blocks`