# Monad Liquid Staking Pool Research

Last updated: 2026-07-01

This note tracks liquid staking and validator-delegation opportunities for the
POSTHUMAN Monad mainnet validator.

- Validator: POSTHUMAN
- Monad mainnet validator ID: 197
- Validator page:
  https://monadvision.com/validator/0xAED164187A9D6314591Ae581A922380A63a1Bd67
- Current commission: 15%

The goal is practical: identify which Monad liquid staking protocols can route
stake to POSTHUMAN, what each protocol needs from a validator, how responsive
the team is, and where POSTHUMAN should spend onboarding effort.

## Executive Summary

| Protocol | Token | Current POSTHUMAN status | Priority | Rationale |
| --- | --- | --- | --- | --- |
| shMonad / FastLane | shMON | Accepted and onboarded. FastLane instructions were received and the MEV sidecar has been installed. | Very high | Clear validator path, direct team response, deterministic on-chain stake allocation, MEV/priority-fee revenue can increase delegation. |
| Kintsu | sMON | Team replied positively and POSTHUMAN is in onboarding. | High | DAO-driven validator curation and a clear Monad LST product. Requires follow-through on onboarding and registry/delegation mechanics. |
| Magma | gMON | Team said to wait for the next batch. | Medium-high | Serious protocol and gVault model, but validator inclusion appears batch/whitelist-based. |
| aPriori | aprMON | Outreach path looks unreliable so far. Tickets did not work cleanly; after direct messages, the server later disappeared from the visible list. | Low-medium | Strong protocol narrative, but validator onboarding path is opaque and current communication friction is high. |
| Moonmace | mcMON | Outreach got no useful response; community looked thin at review time. | Low | Public docs mention a validator scoring matrix, but there is no clear onboarding path and weak observable community signal. |

## Scoring Method

Scores are qualitative and intended for operator prioritization, not investment
advice.

- 5 = actionable now, clear path, good response, material expected value.
- 3 = worth tracking or continuing outreach, but blocked by timing,
  governance, unclear rules, or team response.
- 1 = no clear path or weak signal.

| Protocol | Onboarding clarity | Team response | Delegation upside | Operational fit | Overall |
| --- | ---: | ---: | ---: | ---: | ---: |
| shMonad / FastLane | 5 | 5 | 5 | 4 | 5 |
| Kintsu | 4 | 4 | 4 | 3 | 4 |
| Magma | 3 | 3 | 4 | 4 | 3.5 |
| aPriori | 1 | 2 | 4 | 2 | 2 |
| Moonmace | 2 | 1 | 2 | 3 | 1.5 |

## shMonad / FastLane

shMonad is the clearest current opportunity. FastLane provides a validator
onboarding flow that connects validator revenue generation with shMonad stake
allocation.

### What FastLane Offered

FastLane's onboarding message for POSTHUMAN described:

- 90% of MEV auction revenue goes to the validator's coinbase contract.
- Priority fee distribution depends on validator commission, configurable by
  the validator.
- shMonad delegation is performance-based: more revenue means more stake.
- Stake allocation is on-chain and deterministic.
- The MEV sidecar runs as a separate process and was described as
  Foundation-approved.
- Revenue starts flowing from the next epoch after setup, approximately 5.5
  hours.
- FastLane stated that 118 validators were already running the sidecar at the
  time of onboarding.

### POSTHUMAN Status

POSTHUMAN contacted FastLane/shMonad, was accepted, and received onboarding
instructions. The requested validator details were provided:

- validator ID: 197
- validator location: Tokyo, Japan
- validator peer details: provided directly to FastLane

The FastLane MEV sidecar has been installed for the POSTHUMAN Monad mainnet
validator.

### Validator-Side Requirements

The onboarding flow includes:

1. shMonad/FastLane deploys a validator-specific coinbase contract.
2. Validator sets that coinbase contract as beneficiary in node.toml.
3. Validator restarts monad-bft; RPC/execution restart is not required for
   the beneficiary change.
4. Validator connects FastLane dedicated fullnodes, with peer information
   selected by validator location.
5. Validator runs the MEV sidecar.
6. Validator monitors revenue and commission/donation settings.

### Sources

- shMonad docs: https://docs.shmonad.xyz/
- Validator onboarding:
  https://docs.shmonad.xyz/validators/onboarding
- Sidecar installation:
  https://docs.shmonad.xyz/validators/onboarding/install-sidecar-rootless-docker
- Stake allocation:
  https://docs.shmonad.xyz/stake-allocation
- Revenue dashboard:
  https://analytics.shmonad.xyz/stake-analytics/revenue
- MEV analytics: https://mev-pulse.fastlane.xyz
- Revenue calculator: https://fastlane-revenue-calculator.vercel.app
- Commission portal:
  https://analytics.shmonad.xyz/validator-portal/commission
- FastLane GitHub: https://github.com/FastLane-Labs
- FastLane contracts:
  https://github.com/FastLane-Labs/fastlane-contracts
- FastLane sidecar:
  https://github.com/FastLane-Labs/fastlane-sidecar
- FastLane blog: https://www.fastlane.xyz/blog
- FastLane X: https://x.com/0xFastLane
- FastLane Discord: https://discord.fastlane.xyz

## Magma

Magma is a liquid staking protocol on Monad that issues gMON. Its docs describe
liquid staking, gVaults, and MEV-boosted yield.

### POSTHUMAN Status

POSTHUMAN contacted Magma. The response was to wait for the next validator
batch.

This makes Magma a strong follow-up target, but not an immediate integration.
The practical path is to keep contact warm and prepare a validator profile for
the next inclusion window.

### Validator Fit

Magma appears relevant for POSTHUMAN because:

- gMON is backed by staked MON.
- Magma describes gVaults as validator-specific staking vaults.
- Magma emphasizes MEV-boosted yield.
- gVaults can let users choose a validator while still receiving the fungible
  gMON asset.

The open blocker is validator inclusion: public docs do not currently provide a
simple self-serve validator onboarding form.

### Sources

- Magma site: https://www.magmastaking.xyz/
- Magma docs: https://docs.hydrogenlabs.xyz/magma
- Magma liquid staking:
  https://docs.hydrogenlabs.xyz/magma/liquid-staking-gmon.md
- gVaults docs: https://docs.hydrogenlabs.xyz/magma/gvaults.md
- gVaults app: https://gvaults.magmastaking.xyz/
- gVaults launch article:
  https://blog.magmastaking.xyz/p/gvaults-are-live-staking-vaults-built
- Magma audits:
  https://docs.hydrogenlabs.xyz/magma/developers/audits
- Magma GitHub:
  https://github.com/magmastaking/contracts-public
- Magma X: https://x.com/magmastaking
- Magma Discord: https://discord.com/invite/magmastaking

## Kintsu

Kintsu is a Monad liquid staking protocol that issues sMON and uses a
DAO-driven validator registry / delegation marketplace.

### POSTHUMAN Status

Kintsu replied positively and said POSTHUMAN will be taken into onboarding.
POSTHUMAN is currently in process.

This is the second strongest target after shMonad/FastLane. The important next
step is to clarify exact registry, collateral, voting, and delegation mechanics
for POSTHUMAN.

### Validator Fit

Kintsu is relevant because:

- It is explicitly built for Monad liquid staking.
- It uses sMON as the liquid version of MON.
- Its public docs describe a decentralized registry of validators controlled by
  the DAO.
- Delegation is expected to be community/DAO-curated rather than a simple
  private whitelist.

Operationally, this may require more than technical setup. POSTHUMAN should
expect governance/community work and should confirm whether collateral,
registry staking, or other validator commitments are required.

### Sources

- Kintsu site: https://kintsu.xyz/
- Kintsu staking app: https://kintsu.xyz/staking
- Kintsu docs: https://docs.kintsu.xyz/
- Kintsu on Monad:
  https://docs.kintsu.xyz/supported-blockchains/kintsu-on-monad.md
- Monad LST architecture:
  https://docs.kintsu.xyz/the-kintsu-protocol/architecture-and-integration/monad-lst-architecture.md
- DAO and governance:
  https://docs.kintsu.xyz/the-kintsu-protocol/dao-and-governance.md
- Official contract addresses:
  https://docs.kintsu.xyz/the-kintsu-protocol/official-contract-addresses.md
- Kintsu GitHub: https://github.com/WaterCoolerStudiosInc
- Kintsu audits:
  https://github.com/WaterCoolerStudiosInc/Kintsu-Audits
- Kintsu X: https://x.com/Kintsu
- Kintsu legacy Twitter handle: https://twitter.com/kintsu_xyz
- Kintsu Discord: https://discord.gg/kintsu
- Kintsu Medium: https://medium.com/@kintsu_xyz

## aPriori

aPriori has a strong Monad MEV/liquid staking narrative and aprMON is positioned
as a liquid staking token that accrues staking and MEV revenue.

### POSTHUMAN Status

POSTHUMAN outreach has been problematic so far:

- Ticket creation did not work cleanly.
- After direct messages, the server later disappeared from the visible list.

This does not mean aPriori is a bad protocol. It means POSTHUMAN currently does
not have a reliable validator onboarding route and should not count on this path
until contact is re-established through a confirmed official channel.

### Validator Fit

aPriori remains worth tracking because:

- aprMON combines staking and MEV revenue.
- aPriori focuses on MEV infrastructure and trade execution.
- The protocol may have a curated validator set.

The blocker is process opacity: public docs explain the product, but not a
clear validator application path.

### Sources

- aPriori site: https://www.apr.io/
- aPriori docs: https://apriori-docs.gitbook.io/apriori-docs
- aprMON basics:
  https://apriori-docs.gitbook.io/apriori-docs/aprmon/aprmon-basics.md
- Staking yield:
  https://apriori-docs.gitbook.io/apriori-docs/aprmon/aprmon-basics/staking-yield.md
- aPriori FAQ:
  https://apriori-docs.gitbook.io/apriori-docs/faqs/faq.md
- Stake app: https://stake.apr.io
- aPriori X: https://x.com/aPriori
- aPriori Discord: https://discord.com/invite/apriori

## Moonmace

Moonmace is a smaller Monad liquid staking project with mcMON. Public docs
describe a validator selection matrix, but the observable onboarding signal is
weak.

### POSTHUMAN Status

POSTHUMAN did not receive a useful response. The community looked empty or very
thin at review time.

Moonmace should stay on the watchlist, but it should not consume much operator
time unless the project becomes more active or publishes a clear onboarding
route.

### Validator Fit

Moonmace's public validator strategy is conceptually relevant:

- validators are scored on performance / reliability;
- MEV or priority-fee efficiency matters;
- centralization risk is penalized;
- stake caps are used to reduce concentration.

The problem is not the scoring model. The problem is weak current execution
signal and no clear practical path for POSTHUMAN.

### Sources

- Moonmace docs: https://moonmace.gitbook.io/moonmace-docs
- mcMON liquid staking:
  https://moonmace.gitbook.io/moonmace-docs/liquid-staking-mcmon.md
- Validator strategy:
  https://moonmace.gitbook.io/moonmace-docs/validator-strategy.md
- System architecture:
  https://moonmace.gitbook.io/moonmace-docs/system-architecture.md
- Moonmace X: https://x.com/moonmace_ai

## Recommended Next Actions

1. shMonad / FastLane: monitor revenue, sidecar health, commission, donation
   settings, and stake allocation. Keep the coinbase/beneficiary configuration
   documented internally.
2. Kintsu: continue onboarding. Ask for exact validator registry mechanics,
   collateral requirements, voting/delegation rules, and expected timeline.
3. Magma: prepare a short POSTHUMAN validator profile for the next batch:
   validator ID, validator page, uptime, commission, region, MEV readiness, and
   monitoring setup.
4. aPriori: retry only through a verified official contact. Do not spend
   significant time until the onboarding path is clear.
5. Moonmace: monitor passively. Revisit only if community activity and
   validator onboarding become credible.

## POSTHUMAN Validator Profile for Outreach

Use this compact profile when contacting Monad LST teams:

- Validator: POSTHUMAN
- Monad mainnet validator ID: 197
- Validator page:
  https://monadvision.com/validator/0xAED164187A9D6314591Ae581A922380A63a1Bd67
- Commission: 15%
- Location: Tokyo, Japan
- Operator profile: experienced multi-chain validator with production
  monitoring, active alerting, and existing Monad mainnet operations.
- MEV / priority-fee posture: willing to integrate validator-side revenue
  infrastructure when the operational requirements are clear and safe.
