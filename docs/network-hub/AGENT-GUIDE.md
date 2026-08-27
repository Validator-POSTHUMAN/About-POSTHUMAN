# Guide for AI agents and developers

## Canonical discovery sequence

Use first-party machine-readable files in this order:

1. [`/llms.txt`](https://hub-preview.posthuman.digital/llms.txt) for the short
   product map and boundaries.
2. [`/agent-index.json`](https://hub-preview.posthuman.digital/agent-index.json)
   for current products, network identifiers, API lifecycle, validator
   profiles, and MCP state.
3. [`/llms-full.txt`](https://hub-preview.posthuman.digital/llms-full.txt) for
   detailed route and safety guidance.
4. [`/openapi.json`](https://hub-preview.posthuman.digital/openapi.json) for
   exact API operations, parameters, schemas, errors, freshness, provenance,
   and record caps.
5. [`/validator-profile.json`](https://hub-preview.posthuman.digital/validator-profile.json)
   when the task concerns POSTHUMAN's Cosmos Hub validator identity.

Do not infer an API from frontend traffic, JavaScript bundles, imported guide
text, HAR captures, or an old copy of this documentation.

## Choose the narrowest interface

| Request | Preferred interface |
|---|---|
| Current public chain or validator data | Exact operation from OpenAPI |
| Human-readable network exploration | Canonical Explorer route |
| Node installation or recovery procedure | Node Ops guide, returned for human review |
| POSTHUMAN Cosmos Hub validator identity | Validator profile, then live validator API |
| Available agent instructions | Reviewed skill catalogue on MCP & API |
| MCP tool call | Unavailable until discovery publishes a live endpoint |

## Public API inventory

The deployed contract currently contains 19 fixed `GET` operations:

- IBC: `/api/relayers`, `/api/relayer-performance`.
- Governance: `/api/governance`, `/api/gov-participation`.
- Network observations: `/api/network-watchers`, `/api/chain-params`,
  `/api/network-stats`, `/api/dev-activity`.
- Validator and supply observations: `/api/validators`,
  `/api/slash-observations`, `/api/burn-observations`, `/api/lsm-stats`,
  `/api/rich-list`.
- Node and chain catalogues: `/api/snapshots`, `/api/wasm-assets`.
- Exact detail: `/api/account/{networkId}/{address}`,
  `/api/validator/{networkId}/{operatorAddress}`,
  `/api/tx/{networkId}/{hash}`, and
  `/api/block/{networkId}/{reference}`.

`openapi.json` is authoritative if this summary and the deployed contract ever
differ. Do not invent `/api/v1` aliases or an arbitrary upstream path.

## Safe request procedure

1. Resolve the operation from the current OpenAPI contract.
2. Validate every network ID, chain ID, address, hash, height, reference, and
   denom against that operation.
3. Send a bounded HTTPS `GET` request with a finite timeout.
4. On success, validate `schemaVersion`, requested identity, `generatedAt`,
   `source`, `scope`, status fields, record caps, and `warnings`.
5. Preserve exact integer token values as strings.
6. Surface stale, partial, collecting, unsupported, unavailable, and truncated
   states explicitly.
7. Cache according to the contract and retry only idempotent reads with bounded
   backoff. Treat `429` as a stop-and-wait signal.
8. Cite the canonical route and observation time in the answer.

Minimal example:

```js
const base = 'https://hub-preview.posthuman.digital'
const response = await fetch(`${base}/api/network-watchers`, {
  headers: { accept: 'application/json' },
  credentials: 'omit',
  signal: AbortSignal.timeout(10_000),
})

if (!response.ok) throw new Error(`Hub API ${response.status}`)
const snapshot = await response.json()
if (snapshot.schemaVersion !== 'posthuman.network-watchers/v1') {
  throw new Error('Unsupported schema')
}
console.log(snapshot.generatedAt, snapshot.source)
```

## Error semantics

Handle invalid input (`400`), missing exact resources (`404`), edge limiting
(`429`), invalid or unavailable upstream data (`502`), and temporary service
unavailability (`503`) without converting them into empty successful results.
Some static projections return a successful document whose internal lifecycle
is unavailable or collecting; inspect the schema instead of checking HTTP
status alone.

## MCP lifecycle

[`mcp-tools-planned.json`](https://hub-preview.posthuman.digital/mcp-tools-planned.json)
maps the same 19 OpenAPI operations to proposed read-only tools. It is a design
inventory only. In the current discovery record:

- `state` is `planned`;
- `endpoint` is `null`;
- `serverCard` is `null`;
- `transport` is `null`;
- `authentication` is `null`.

Do not invent a connection URL, tool transport, OAuth flow, API key, or server
capability. Continue using HTTPS `GET` operations until discovery explicitly
changes the lifecycle to available.

## Skills

The MCP & API page lists 18 immutable reviewed public skills: ten network
skills and eight operation skills. A skill is a readable instruction package,
not remote code execution and not proof that the current environment grants
its requested tools or permissions.

The reviewed source repository is
[`Validator-POSTHUMAN/AI-skills-for-networks`](https://github.com/Validator-POSTHUMAN/AI-skills-for-networks).
Use the revision and checksum published by the Hub rather than an unpinned
branch URL when binding a skill to an automated workflow.

Before using a skill:

1. Select the smallest skill matching the task.
2. Inspect its source, immutable revision, and `SKILL.md` SHA-256.
3. Read its complete instructions and referenced required files.
4. Preserve the user's authority, approval, secret, transaction, and
   production boundaries.
5. Reverify live chain and service state; a skill does not replace current
   evidence.

## Node Ops boundary

An agent may retrieve and explain a Node Ops guide. It must not infer host
access or authorization to execute commands. Before any real validator action,
the operator must bind the exact target, current state, key and signer risks,
backup and rollback plan, and approval required by that action.

Never ask for or transmit a seed phrase, private key, validator consensus key,
keyring, password, cookie, or internal host detail.

## Wallet boundary

API and Node Ops reads do not authorize a transaction. If a user explicitly
chooses a supported browser wallet action, preserve the two-stage human review:
fresh simulation and Hub confirmation, followed by wallet approval. Never
automate consent, silently broaden a message, retry a broadcast without a new
decision, or treat a connected wallet as general authority.

## Example agent requests

- “List current Cosmos Hub governance proposals from the Hub API. Include
  `generatedAt`, source, and any warnings.”
- “Open the POSTHUMAN Cosmos Hub validator profile, then verify mutable status
  using its live-data URL.”
- “Compare developer activity for the reviewed repositories, but state why it
  is not a quality or investment score.”
- “Find the Node Ops snapshot guide for a selected network and return a
  review checklist. Do not run commands.”
- “Generate a typed client from the pinned OpenAPI contract and fail closed on
  unknown schema versions.”

## Prohibited assumptions

Do not claim that the Hub provides private validator topology, signing keys,
custody, unattended signing, unattended broadcast, node control, deployment,
guaranteed performance, guaranteed yield, endorsement, or a live MCP server.
