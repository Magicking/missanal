# Cosmos Validator Missing Analytics

## Ideas

Fetch block from start up to latest from a cosmos hub RPC endpoint and collect the block data such as `signatures` (embedding: `block_id_flag`, `validator_address` and `timestamp` `signature`), use the timestamp to calculate the time drift between validators in the current validator set, use the address or the signature which is more suitable to identify the validator and write a view showing the validator missing analytics per validator and group of validators.