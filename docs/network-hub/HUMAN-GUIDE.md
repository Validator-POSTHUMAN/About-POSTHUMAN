# Guide for people

## Start with a goal

| Goal | Start here |
|---|---|
| Find a network or validator | [Explorer](https://hub-preview.posthuman.digital/explorer) |
| Install or maintain a node | [Node Ops](https://hub-preview.posthuman.digital/node-ops) |
| Inspect the public API or skills | [MCP & API](https://hub-preview.posthuman.digital/mcp-api) |
| Review public address holdings | [Portfolio](https://hub-preview.posthuman.digital/portfolio) |
| Inspect NFTs | [NFT](https://hub-preview.posthuman.digital/nft) |
| Compare public repository activity | [Developer Activity](https://hub-preview.posthuman.digital/explorer/cosmoshub/dev-activity) |

## Explore a network

1. Open Explorer and select a network.
2. Use the network menu to choose validators, blocks, transactions, accounts,
   governance, consensus, RPC, parameters, assets, or another available view.
3. Check the displayed chain ID and freshness before using a value elsewhere.
4. Follow the source or canonical detail link when you need independent
   confirmation.

Explorer search accepts identifiers such as a supported address, transaction
hash, block height or hash, proposal, contract, or asset. Use the exact
network context: a familiar ticker or address prefix is not enough to prove
chain identity.

## Review a validator

Open the validator list for the exact network and select a validator detail
page. Status, rank, voting power, commission, missed blocks, rewards, and other
fields are mutable observations. Confirm their timestamp and source.

The machine-readable POSTHUMAN Cosmos Hub identity is available at
[validator-profile.json](https://hub-preview.posthuman.digital/validator-profile.json).
It provides verified identity and routing, not a performance or yield
guarantee.

## Use Node Ops safely

1. Select the exact network and Node Ops section.
2. Read prerequisites and identify whether the material is a guide, public
   endpoint, bootstrap artifact, or copy-only command.
3. Reconfirm the current official release, checksum, chain ID, upgrade plan,
   storage requirement, and service layout.
4. Before validator work, prove that only one signer can use the consensus
   key. Preserve keys, configuration, signer state, backups, and rollback.
5. Run commands yourself in the intended environment and verify the result.

The Hub does not execute Node Ops commands and cannot see your server. A
published snapshot or endpoint can become stale or unavailable; use the
status and integrity information shown next to it.

## Use the public API

The [MCP & API directory](https://hub-preview.posthuman.digital/mcp-api)
supports search by path, operation, and schema. Open an operation to review its
purpose, parameters, response type, provenance, freshness, and record cap.

For development work, use the
[OpenAPI contract](https://hub-preview.posthuman.digital/openapi.json) and
[client guide](https://hub-preview.posthuman.digital/api-client-guide.md).
The contract currently contains 19 unauthenticated read-only `GET` operations.
It is not an arbitrary chain proxy.

## Understand Developer Activity

Developer Activity reports 52 weekly non-merge commit buckets and bounded
linked-contributor counts for one fixed primary public repository per Explorer
network. You can search and sort the observations.

Use it as a narrow repository-activity signal only. Repository selection,
mirrors, monorepos, contribution patterns, generated commits, and GitHub API
availability can affect the result. Do not use the ranking as a project-quality
or investment score.

## Review a wallet action

Wallet actions are optional and user initiated. Before approving:

1. Confirm the wallet account and chain.
2. Read the exact message type, validator or recipient, amount, denom, and
   authorization scope.
3. Review simulation, gas limit, and fee.
4. Confirm in the Hub only if the preview is correct.
5. Confirm again in the wallet and independently verify the resulting
   transaction.

Never enter a seed phrase or private key. A support request that asks for one
is not part of the Hub workflow.

## Troubleshooting

- **Unavailable or stale data:** wait for the next collector observation or
  verify through the linked public source. Do not reinterpret it as zero.
- **Unsupported network action:** use the read-only view; do not transplant a
  transaction flow from another chain.
- **API error:** check the HTTP status and JSON `error`, then validate the
  exact input against OpenAPI.
- **No MCP connection:** expected. MCP is planned and no public endpoint is
  advertised.
- **Missing Node Ops field:** treat `Not published` as an explicit boundary,
  not permission to guess.
