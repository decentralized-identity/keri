# KID0006 - Seals - Commentary


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
|[0006](kid0006.md)|X|Seals|
|[0007](kid0007.md)|[X](kid0007Comment.md)|Delegation (pending PR by Sam)|
|[0008](kid0008.md)|[X](kid0008Comment.md)|Key-Event State Machine|
|[0009](kid0009.md)|[X](kid0009Comment.md)|Indirect Mode & Witnesses|
|0010||Recovery/consensus Algorithm (KAACE)|
|0011||Database & Storage Considerations|
|0097|n/a|**Non-Normative** Implementation Guidance|
|0098|n/a|Use Cases|
|0099|n/a|Test Vectors and Normative Statement Index|

## Rationale for Seals

The interpretation of the data associated with the digest or hash tree root in the seal is independent of KERI. This allows KERI to be agnostic about anchored data semantics. Another way of saying this is that seals are data agnostic; they don’t care about the semantics of its associated data. This better preserves privacy because the seal itself does not leak any information about the purpose or specific content of the associated data. Furthermore, because digests are a type of content address, they are self-discoverable. This means there is no need to provide any sort of context or content specific tag or label for the digests. Applications that use KERI may provide discovery of a digest via a hash table (mapping) whose indexes (hash keys) are the digests and the values in the table are the location of the digest in a specific event. To restate, the semantics of the digested data are not needed for discovery of  the digest within a key event sequence.

To elaborate, the provider of the data understands the purpose and semantics and may disclose those as necessary, but the act of verifying authoritative control does not depend on the data semantics merely the inclusion of the seal in an event. It’s up to the provider of the data to declare or disclose the semantics when used in an application. This may happen independently of verifying the authenticity of the data via the seal. This declaration may be provided by some external application programmer interface (API) that uses KERI. In this way, KERI provides support to applications that satisfies the spanning layer maxim of minimally sufficient means. Seals merely provide evidence of authenticity of the associated (anchored) data whatever that may be. 

This approach follows the design principle of context independent extensibility. Because the seals are context agnostic, the context is external to KERI. Therefore the context extensibility is external to and hence independent of KERI. This is in contrast to context dependent extensibility or even independently extensible contexts that use extensible context mechanisms such as linked data or tag registries [96; 114; 118; 149]. Context independent extensibility means that KERI itself is not a locus of coordination between contexts for anchored data. This maximizes decentralization and portability. Extensibility is provided instead at the application layer above KERI though context specific external APIs that reference KERI seals in order to establish control authority and hence authenticity of the anchored (digested) data. Each API provides the context not KERI. This means that interoperability within KERI is focused solely on interoperability of control establishment. But that interoperability is total and complete and is not dependent on anchored data context. This approach further reflects KERI’s minimally sufficient means design aesthetic.