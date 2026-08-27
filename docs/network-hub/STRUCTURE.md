# Structure and trust model

## Logical architecture

```text
People and AI agents
        |
        v
Public Network Hub routes
  |-- Explorer
  |-- Node Ops
  |-- MCP & API
  |-- Portfolio and NFT
        |
        +--> reviewed static catalogues and guides
        +--> fixed same-origin read-only API projections
        +--> optional user-controlled browser wallet flow
```

The Hub presents public information through one product shell while keeping
different authority levels separate. A page that explains an operation does
not gain authority to execute it, and an API response does not grant wallet or
host access.

## Product layers

### Network discovery

The home, mainnet, and testnet catalogues route users to a canonical network
workspace. Records come from reviewed public registries and contributions.
Unknown fields stay unavailable instead of being inferred from another
network.

### Explorer

Explorer owns public chain-data views. Depending on the selected network and
available sources, these can include:

- validators and validator detail;
- blocks, transactions, accounts, governance, and upgrades;
- consensus and network observations;
- public RPC checks;
- chain parameters, supply, liquid staking, and burn or slash observations;
- decentralization, rich-list, CosmWasm, and asset projections;
- relayer routes and bounded managed-path observations;
- developer activity for fixed reviewed repositories.

The supported Explorer identifiers currently published by agent discovery are
`cosmoshub`, `osmosis`, `neutron`, `axelar`, `celestia`, `juno`, `mantra`,
`atomone`, `oraichain`, and `verona`.

### Node Ops

Node Ops owns operational knowledge: installation, bootstrap files, endpoints,
ports, seeds, state sync, snapshots, upgrades, monitoring, security, multisig,
REStake, relayers, and related guides.

These are review-and-copy instructions. The Hub has no SSH session, private
inventory, keyring, service manager, firewall controller, or unattended
recovery path. An operator must verify current official releases, checksums,
on-chain plans, backups, signer uniqueness, storage, and rollback before using
a command.

### MCP & API

The merged MCP & API surface has three distinct parts:

1. A live public OpenAPI-backed directory containing 19 fixed `GET`
   operations.
2. A planned read-only MCP mapping for the same 19 operations.
3. A catalogue of 18 immutable reviewed skills: ten network skills and eight
   operation skills.

The API is callable now. The MCP mapping is not. Skills are readable local
instruction packages; installing a skill does not grant a remote agent access
to POSTHUMAN infrastructure.

### Portfolio and NFT

Portfolio reads public account state. NFT views identify or display bounded
public NFT records with restricted media handling. These surfaces do not
provide custody.

### Browser wallet boundary

Some Cosmos Hub Explorer actions can construct an allowlisted transaction in
the browser. The user must connect a compatible wallet, review a fresh
simulation and fee, confirm inside the Hub, and approve again in the wallet.
The Hub does not store or receive the signing key and has no server-side
signer. Other networks remain read-only until their behavior is separately
reviewed.

## Data classes

| Class | Examples | Consumer rule |
|---|---|---|
| Reviewed static data | network identity, guides, public skill metadata | Verify the published source and revision |
| Collector projection | validators, governance, snapshots, activity, network statistics | Check timestamp, source, scope, status, caps, and warnings |
| Exact detail query | account, validator, transaction, block | Bind the response to the exact network and requested identifier |
| Browser-only external read | optional market or RPC checks | Treat failure as unavailable; do not silently substitute another network |
| Browser wallet action | reviewed Cosmos Hub transactions | Require simulation and explicit user approval; never automate consent |

## Freshness and failure model

The Hub prefers explicit partial, stale, collecting, unsupported, unavailable,
or truncated states over invented completeness. Consumers should not convert
one of those states into zero, an empty chain, or a negative fact.

Exact integer token amounts can exceed safe JavaScript number precision and
should remain strings until a decimal library processes them. Mutable values
such as validator status, commission, voting power, balances, rewards, prices,
and network height must be read from current data rather than copied into a
long-lived assumption.

## Public security boundary

The Hub does not expose:

- arbitrary RPC or REST proxying;
- private hosts or validator topology;
- credentials, wallet sessions, or key material;
- unattended signing or broadcast;
- deployment, service control, firewall control, or data replacement;
- guaranteed validator rank, performance, yield, or endorsement.

An independently deployed MCP service would require a published endpoint,
transport, Server Card, authentication decision, rate limits, capability
state, and verification. Until discovery metadata changes, clients must treat
MCP as planned.
