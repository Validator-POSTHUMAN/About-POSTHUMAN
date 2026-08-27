# POSTHUMAN Network Hub

POSTHUMAN Network Hub is a public interface for exploring supported networks,
reading chain and validator data, reviewing node-operation guides, using a
fixed read-only API, and discovering reviewed instructions for AI agents.

Open the Hub: <https://hub-preview.posthuman.digital/>

The current hostname identifies the service as a public preview. Consumers
must treat routes, schemas, freshness metadata, and lifecycle states as the
source of truth instead of inferring availability from this document.

## Documentation map

| Guide | Audience | Purpose |
|---|---|---|
| [Structure and trust model](STRUCTURE.md) | Everyone | Products, data flow, provenance, and security boundaries |
| [Guide for people](HUMAN-GUIDE.md) | Visitors and operators | How to explore networks, inspect data, use guides, and review wallet actions |
| [Guide for agents](AGENT-GUIDE.md) | AI agents and developers | Discovery order, API workflow, MCP status, skills, validation, and limits |

## What is available

| Surface | Current role |
|---|---|
| [Explorer](https://hub-preview.posthuman.digital/explorer) | Public chain, validator, governance, account, transaction, block, asset, RPC, and network observations |
| [Node Ops](https://hub-preview.posthuman.digital/node-ops) | Reviewed copy-only node and validator-operation guidance |
| [MCP & API](https://hub-preview.posthuman.digital/mcp-api) | Searchable directory for 19 public `GET` operations, 19 planned MCP mappings, and 18 reviewed public skills |
| [Portfolio](https://hub-preview.posthuman.digital/portfolio) | Read-only balances, delegations, unbonding, and rewards for public addresses |
| [NFT](https://hub-preview.posthuman.digital/nft) | Wallet-scoped NFT identification and gallery views |
| [Developer Activity](https://hub-preview.posthuman.digital/explorer/cosmoshub/dev-activity) | Bounded primary-repository activity for the ten Explorer networks |

Developer Activity is an observation of one reviewed public repository per
network. It is not a score for code quality, team productivity, delivery,
decentralization, or investment merit.

## Current machine interfaces

- [Agent discovery index](https://hub-preview.posthuman.digital/agent-index.json)
- [Short agent guide](https://hub-preview.posthuman.digital/llms.txt)
- [Detailed agent guide](https://hub-preview.posthuman.digital/llms-full.txt)
- [OpenAPI 3.1 contract](https://hub-preview.posthuman.digital/openapi.json)
- [API client guide](https://hub-preview.posthuman.digital/api-client-guide.md)
- [Planned MCP tool map](https://hub-preview.posthuman.digital/mcp-tools-planned.json)
- [Reviewed skill sources](https://github.com/Validator-POSTHUMAN/AI-skills-for-networks)
- [POSTHUMAN Cosmos Hub validator profile](https://hub-preview.posthuman.digital/validator-profile.json)
- [Sitemap](https://hub-preview.posthuman.digital/sitemap.xml)

The public REST API is available and contains fixed read-only `GET`
operations. MCP is not available yet: no endpoint, Server Card, transport, or
authentication model is advertised. The MCP JSON file is a reviewable design
inventory, not a callable server.

## Safety summary

- Never provide a mnemonic, private key, validator key, keyring, password,
  cookie, or internal host detail to the Hub or an agent.
- Node Ops does not connect to a host, operate a validator, restart a service,
  replace data, or move a key.
- API reads do not authorize signing, broadcast, deployment, or node control.
- Wallet actions exist only for explicitly reviewed browser flows. They require
  user connection, simulation, in-app review, and a separate wallet approval.
- Chain state changes. Verify chain ID, height, timestamp, source, warnings,
  address, denom, fee, and simulation before acting.

## Sources of truth

Use the narrowest authoritative source for each question:

1. The live route for the selected product and network.
2. `openapi.json` for API paths, parameters, response schemas, and errors.
3. `agent-index.json` for current product and MCP lifecycle states.
4. Response `schemaVersion`, `generatedAt`, `source`, `scope`, and `warnings`
   for data quality and provenance.
5. Linked official project documentation for protocol-level behavior.

This repository documents the public product. It does not publish the Hub's
private deployment topology, service credentials, validator infrastructure,
or signing systems.
