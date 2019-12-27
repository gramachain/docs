---
title: Consensus
has_children: false
nav_order: 3
---

# Consensus

Nodes should not accept blocks or transactions that do not conform to these guidelines.

When creating a new block a delegate must add a reward transaction as the very first transaction in the block that is a sum of all accepted transactions with a zero amount.  

If there is a forfeiture of a bond then that transaction must be placed as the second transaction and should be included in block reward calculations with a zero amount and the fee the sum of the bond.

The bond amount is listed on the fee schedule and should be sent by the delegate before block creation to the next delegate.  The next delegate is only allowed to include the transaction as a forfeit transaction if the current delegate doesn't produce a valid block otherwise the transaction should expire.

Blocks and transactions must be under a maximum defined size to keep performance at optimal levels.   All block information will be kept by all delegates and full nodes.  Blocks can be created and validated as fast as possible but must not surpass a defined time limit.

For consensus to be reached among elected delegates in a term on any given round 2/3 yes votes must be received for a block to be considered valid.  Votes will be included with the block during storage and in broadcasting to the network so that other accounts can validate the delegate signatures.

Once a block has been submitted to the network the next delegate with start the consensus cycle over.