# BIPMAD
Bitcoin Improvement Proposal Modifications and Deletions for BSHA3

> For anything unmentioned, BSHA3 corresponds to Bitcoin.

Here is a listing of chain nuances:

- BIP34 is always enabled. However, for blocks under 16, `push_int64` is instead used of the encoding in the original BIP. The genesis block is also mined with a `CScriptNum(0)` for conformance. See: https://github.com/bitcoin/bitcoin/pull/14633 for Bitcoin's discussion.

- Although it calculates the hashes of the leaves using `SHA3d`, BSHA3 performs the reduction step of merkle root calculation using `SHA256d`. Satoshi's classic Merkle Tree implementation (standard, leaf-node weakness) is used.

- CSV (BIP 68, 112, 113) is always enabled. This means its code has been migrated out of the BIP9-activation path.

- Segwit is always enabled. This means its code has been migrated out of the BIP9-activation path.

- The Segwit witness commitment prefix has been changed to `0f0f0f0f0f0f`, from Bitcoin's `6a24aa21a9ed`. This is for simplicity only. See: https://github.com/bitcoin/bips/blob/master/bip-0141.mediawiki#commitment-structure for Bitcoin's specification.

- Addresses are in a modified `base58check` format - the checksum is calculated by 2 rounds of SHA3-256 instead of SHA256.
