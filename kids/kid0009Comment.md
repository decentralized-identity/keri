# KID0009 - Indirect Mode & Witnesses - Commentary

## Navigation

[Back to table of contents](readme.md)
|Link|Commentary|Section
|---|---|---|
|[0000](kid0000.md)|[X](kid0000Comment.md)|Glossary, overview, how to use|
|[0001](kid0001.md)|[X](kid0001Comment.md)|Prefixes, Derivation and derivation reference tables|
|[0002](kid0002.md)|[X](kid0002Comment.md)|Data model (field & event concepts and semantics)|
|[0003](kid0003.md)|[X](kid0003Comment.md)|Serialization|
|[0004](kid0004.md)|[X](kid0004Comment.md)|Key Configuration (Signing threshold & key set)|
|[0005](kid0005.md)|[X](kid0005Comment.md)|Next Key Commitment (Pre-Rotation)|
|[0006](kid0006.md)|[X](kid0006Comment.md)|Seals|
|[0007](kid0007.md)|[X](kid0007Comment.md)|Delegation (pending PR by Sam)|
|[0008](kid0008.md)|[X](kid0008Comment.md)|Key-Event State Machine|
|[0009](kid0009.md)|X|Indirect Mode & Witnesses|
|0010||Recovery/consensus Algorithm (KAACE)|
|0011||Database & Storage Considerations|
|0097|n/a|**Non-Normative** Implementation Guidance|
|0098|n/a|Use Cases|
|0099|n/a|Test Vectors and Normative Statement Index|

### Indirect Mode Rationale

While a decentralized total ordering distributed consensus ledger may provide such highly available trustworthy service (key event history) by combining the promulgation and conformation into one set of nodes, it may not be the minimally sufficient means for doing so. As discussed previously, total ordering distributed consensus algorithms either suffer from relatively high latency and low throughput or may not scale well with an increasing number of nodes.

They may be relatively complex and/or expensive to setup and operate. 

This work describes an alternative approach that uses redundant immutable key event receipt logs (KERLS) to provide such a highly available trustworthy service using minimally sufficient means. The separation of promulgation and confirmation into two separate loci-of-control, one the controller’s, and the other the validator’s simplifies the interaction space between these two parties. This architecturally decentralizes the system and provides for better scalability and performance. As a result the service function may have relatively higher throughput, lower latency, better scalability, lower cost and lower complexity than a totally ordered distributed consensus ledger. Notwithstanding the fact that this work removes the need for a totally ordered distributed consensus ledger, it may still use one when other factors or constraints make it desirable.

To elaborate on the blockchain/ledger oracle example, the design principle of separating the loci-of-control between controllers and validators removes one of the major drawbacks of total ordered distributed consensus algorithms, that is, shared governance over the pool of nodes that provide the consensus algorithm.

Removing the constraint of forced shared governance allows each party, controller and validator, to select the level of security, availability, performance specific to their needs. The validator’s confirmation service may be further enhanced to provide duplicity detection and other protections as needed. This is shown in the following diagram:

![](https://i.imgur.com/WPllKzd.png)

### Further Implementation Guidance on Witness Lists

The critical insight is that because the controller is the sole source of truth for the creation of any and all key events, it alone, is sufficient to order its own key events. Indeed, a key event history does not need to provide double spend proofing of an account balance, merely consistency. Key events by in large are idempotent authorization operations as opposed to non-idempotent account balance decrement or increment operations. Total or global ordering may be critical for non-idempotency, whereas local ordering may be sufficient for idempotency especially to merely prove consistency of those operations. The implication of these insights is that fault tolerance may be provided with a single phase agreement by the set of witnesses instead of a much more complex multi-phase commit among a pool of replicants or other total ordering agreement process as is used by popular BFT algorithms [16; 39; 42; 47; 59; 113; 121; 142]. Indeed the security guarantees of an implementation of KA2CE may be designed to approach that of other BFT algorithms but without their scalability, cost, throughput, or latency limitations. If those other algorithms may be deemed sufficiently secure then so may be KA2CE. Moreover because the controller is the sole source of truth for key events, a validator may hold that controller (whether trusted or not) accountable for those key events. As a result, the algorithm is designed to enable a controller to provide itself with any degree of protection it deems necessary given this accountability. 

In the event of a detected duplicitous copy, the validator may then choose how to best protect itself from harm. A special case is a malicious controller that intentionally produces alternate key event histories. Importantly, observer components that maintain copies of the key event history such as watchers, jurors, and judges, may be under the control of validators not controllers. As a result a malicious alternate (duplicitous) event history may be eminently detectable by any validator. We call this ambient duplicity detection (which stems from ambient verifiability). In this case, a validator may still be protected because it may still hold such a malicious controller accountable given a duplicitous copy (trust or not trust). It is at the validator’s discretion whether or not to treat its original copy as the authoritative one with respect to any other copy and thereby continue trusting or not that original copy. A malicious controller may not therefore later substitute with impunity any alternate copy it may produce. Furthermore, as discussed above, a malicious controller that creates an alternative event history imperils any value it may wish to preserve in the associated identifier. It is potentially completely self-destructive with respect to the identifier. A malicious controller producing a detectably duplicitous event history is tantamount to a detectable total exploit of its authoritative keys and the keys of its witness set. This is analogous to a total but detectable exploit of any BFT ledger such as a detectable 51% attack on a proof-of-work ledger. A detectable total exploit can destroy much or all of the value in that ledger after the point of exploit. 