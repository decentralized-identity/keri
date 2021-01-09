# KID0007 - Delegation - Commentary

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
|[0007](kid0007.md)|X|Delegation (pending PR by Sam)|
|[0008](kid0008.md)|[X](kid0008Comment.md)|Key-Event State Machine|
|[0009](kid0009.md)|[X](kid0009Comment.md)|Indirect Mode & Witnesses|
|0010||Recovery/consensus Algorithm (KAACE)|
|0011||Database & Storage Considerations|
|0097|n/a|**Non-Normative** Implementation Guidance|
|0098|n/a|Use Cases|
|0099|n/a|Test Vectors and Normative Statement Index|

## Delegation Rationale

The delegated identifier prefix is a type of self-addressing self-certifying prefix (See Kid0001Comment). This binds the delegated identifier to its delegating identifier. The delegating identifier controller retains establishment control authority over the delegated identifier in that the new delegated identifier may only authorize non-establishment events with respect to itself. Delegation therefore authorizes revokable signing authority to some other self-certifying identifier. The delegated identifier may have its own delegated key event sequence where the inception event is a delegated inception and any rotation events are delegated rotation events. Control authority for the delegated identifier therefore requires verification of a given delegated establishment event which in turn requires verification of the delegating identifier’s establishment event subsequence.

Because the delegation seal in the data payload of the delegating event includes a digest of the full delegated event, it thereby provides a **forward cryptographic commitment** to the delegated identifier as well as any permissions and other configuration data in its associated event. The delegation seal included in the delegated event provides a **backward reference** to the delegating event’s unique location. This uniquely establishes which event in the delegating event log holds the corresponding seal. This provides a type of cross reference that enables a verifier to look up the delegating event and verify the existence of the delegation seal in the list of seals in that delegating event and then verify that the event seal digest is a digest of the delegated event.