# BIPMAD
Bitcoin Improvement Proposal Modifications and Deletions for BSHA3

> For unmentioned BIPs, BSHA3 corresponds to Bitcoin.

Here is a listing of chain nuances:

- BIP34 is always enabled. However, for blocks under 16, `push_int64` is instead used of the encoding in the original BIP. The genesis block is also mined with a `CScriptNum(0)` for conformance. See: https://github.com/bitcoin/bitcoin/pull/14633 for Bitcoin's discussion.

- `SHA256d` is still used in calculation of the tx Merkle Root.

- CSV (BIP 68, 112, 113) is always enabled. This means its code has been migrated out of the BIP9-activation path.

- Segwit is always enabled. This means its code has been migrated out of the BIP9-activation path.

- The Segwit witness commitment prefix has been changed to `0f0f0f0f0f0f`, from Bitcoin's `6a24aa21a9ed`. This is for simplicity only. See: https://github.com/bitcoin/bips/blob/master/bip-0141.mediawiki#commitment-structure for Bitcoin's specification.

