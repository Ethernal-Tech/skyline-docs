---
description: >-
  Considerations related to system scalability, performance characteristics, and
  design trade-offs.
---

# Scalability & Performance

Skyline's performance envelope is set less by raw compute than by two external constraints: the finality characteristics of the chains it bridges and the transaction space available on each. Most of the system's design decisions are readable as responses to one of the two.

### Finality is the dominant latency term

End-to-end bridging time is dominated by waiting, not by processing. Before a source-chain event can be acted on it must be deep enough to be irreversible, and that depth is a solvency parameter rather than a UX one: acting on a transaction that is later reorganised out would mint or release assets on the destination with no backing locked on the source, and there is no clean recovery from that state. The confirmation depth is therefore set by the security model of each chain and cannot be tuned away for speed. These are properties of the chains being bridged, not of the bridge. Any design spanning probabilistic-finality chains inherits the same floor.

### Batching amortises fixed cost, and is tuned conservatively

Throughput comes from grouping. Oracles collect claims and submit them in groups. On Solana a single `bridge_transaction` serves up to three recipients, with other chains being able to cover up to five recipients.

These numbers sit below what the chains would accept in the best case. They are sized against worst-case account and signature footprints so a batch is always includable, rather than against average case with retry on overflow — predictable inclusion is worth more than a marginally larger batch that sometimes fails.

### Extensibility scales unevenly

Growth along the three available axes costs very different amounts of work, and the architecture is explicitly optimised for the two cheapest.

* New tokens are configuration plus a transaction
* New chains of an existing type are just configuration
* New chain types are a vertical slice through every layer
* Validator set changes are the most expensive

