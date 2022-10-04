# Cosmos Validator Missing Analytics

The goal of this project is to show analytics that we are usually missing (miss anal) on various Cosmos dashboard, mainly time drift between validators and groups of validator missing the same block.

## Ideas

Fetch block from START up to LATEST from a cosmos hub RPC endpoint and collect the block data: `signatures` (embedding: `block_id_flag`, `validator_address` and `timestamp` `signature`), use the timestamp to calculate the time drift between validators in the current validator set, use the address or the signature which is more suitable to identify the validator and write a view showing the validator missing analytics per validator and group of validators.

So output shall display Validators time drift related to proposer
and display the groups of validator missing at least N blocks

Example:

Time drift (sorted list, most drift first) between validators and proposer:
Proposer: Val1
Val4: -2ms
Val2: +2ms
Val3: +1ms

Missing blocks:
VAL1 #####M#####
VAL2 #######M###
VAL3 #####M#M###
VAL4 #######M###

For N=2
Output: (VAL1,VAL3),(VAL2,VAL3,VAL4)

For N=3
Output: (VAL2,VAL3,VAL4)

NB: At first public key or hash will be displayed but ultimately we will use the validator name.

# Inputs

 - START TIME: Beginning of the analysis period (either in block height or in time)
 - STOP TIME: End of the analysis period // Will always be latest in the initial phase of the project
 - N: Threshold number of common blocks missing to be considered as a group of validators missing the same block

# Frameworks

 - Golang
 - Cosmos-SDK
 - Cobra