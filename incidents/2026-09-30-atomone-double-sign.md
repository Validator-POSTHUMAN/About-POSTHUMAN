# AtomOne validator incident: duplicate vote and jailing

- **Published:** 30 September 2026 (UTC)
- **Network:** AtomOne mainnet (`atomone-1`)
- **Validator:** [POSTHUMAN](https://www.mintscan.io/atomone/validators/atonevaloper1vcp7pkg8sk0n8ylhezxxs8qqrnwfld4dsv2sew) (`atonevaloper1vcp7pkg8sk0n8ylhezxxs8qqrnwfld4dsv2sew`)

POSTHUMAN's AtomOne validator was jailed after the network accepted evidence of two different prevotes signed by its consensus key for the same height and round. We are publishing the verified sequence, the POSTHUMAN team's allegation, and the limits of the current investigation. **The on-chain evidence establishes double-signing by the key; it does not establish who operated the second signer, how the key became available, or whether the act was deliberate.**

## What happened

On **30 September 2026 at 00:53:24 UTC**, the consensus key associated with POSTHUMAN signed two different `PREVOTE` messages for **height 10,584,953, round 0**. The votes referenced distinct block IDs:

| Vote | Signed timestamp (UTC) | Block ID |
| --- | --- | --- |
| A | 00:53:24.460259433 | `CC1931BAA302AE931BC41DE68AE0A3B0263FDC46B0C82DF8CB2F215CCC3240FF` |
| B | 00:53:24.300958676 | `FB2522A2B1D81E1863118F7BA8D46F46BF6795D08509DD0CEA4E7E7F19FEEF27` |

Both votes carry consensus address `11F825671446CDF9BDD0BA88DD512FF050759D4D`. The network included `DuplicateVoteEvidence` in [block 10,584,954](https://atomone-rpc.publicnode.com/block?height=10584954), whose timestamp is **00:53:24.742453892 UTC**. Our node reported the evidence at approximately **00:53:30 UTC**.

The [on-chain validator record](https://atomone-rest.publicnode.com/cosmos/staking/v1beta1/validators/atonevaloper1vcp7pkg8sk0n8ylhezxxs8qqrnwfld4dsv2sew), checked on 30 September, reports **jailed** and **unbonding**. It lists **21 October 2026 at 00:53:24.742453892 UTC** as the unbonding time. This timestamp is not a promise of recovery or an unjail date; check the live chain record for later changes.

After confirming the evidence, POSTHUMAN **stopped the known production signer at 02:00 UTC** on 30 September and kept it offline to prevent further signing risk. We did not restart it, reset signer state, move keys, or submit an unjail transaction.

## What the investigation has and has not established

Our read-only review found that a separate AtomOne mainnet RPC process was synchronized at the incident height, but its configured local signer state remained at height zero and it had no configured remote signer. That process's presence is **not evidence that it signed either vote**. The source of the second signature remains unidentified.

The production signer's journal recorded conflicting-vote warnings. The available host logs cannot prove who signed a vote or rule out a previously running process, another key location, or a signer-state failure. We are preserving evidence and reviewing historical key custody and signing paths without disclosing or exporting secret material.

A wallet mnemonic and a CometBFT consensus signing key are not interchangeable. Possession of a wallet mnemonic alone does not prove the ability to sign consensus votes. The technical investigation has not attributed the incident to a person, another validator, or a motive.

## Statement from the POSTHUMAN team

On 30 September, POSTHUMAN management alleged that a former team member known as Olim, whom it associates with the validator "Chiter in Cosmos," deliberately caused the AtomOne double-sign. The team says he previously had access to a POSTHUMAN validator wallet mnemonic. The team also reports that, shortly after our validator was jailed, channels associated with "Chiter in Cosmos" urged delegators to redelegate to them.

**These are the team's allegations, not independently verified findings.** We have not published records establishing Olim's access to this AtomOne consensus signing key, a connection between him or that validator and either conflicting vote, or archived links establishing the authorship and timing of the reported redelegation messages. The reported messages, even if authenticated, would not by themselves prove control of the consensus key or intent to double-sign. We invite relevant parties to provide dated, verifiable records and will correct this statement if evidence warrants it.

## Status and next steps

- The known signer remains offline while the signing source and key custody are investigated.
- We are preserving the on-chain evidence and relevant operational logs, and checking every historical location where the consensus key could have existed.
- We will publish material findings and corrections with dates and sources. Any recovery or retirement decision will be handled separately with double-sign safety as the first constraint.
- Delegators should consult the [live validator record](https://www.mintscan.io/atomone/validators/atonevaloper1vcp7pkg8sk0n8ylhezxxs8qqrnwfld4dsv2sew) for current status; the status in this article is a dated snapshot.

## Public evidence

1. [AtomOne block 10,584,954 and `DuplicateVoteEvidence`](https://atomone-rpc.publicnode.com/block?height=10584954).
2. [AtomOne staking validator record](https://atomone-rest.publicnode.com/cosmos/staking/v1beta1/validators/atonevaloper1vcp7pkg8sk0n8ylhezxxs8qqrnwfld4dsv2sew).
3. [POSTHUMAN validator explorer page](https://www.mintscan.io/atomone/validators/atonevaloper1vcp7pkg8sk0n8ylhezxxs8qqrnwfld4dsv2sew).
