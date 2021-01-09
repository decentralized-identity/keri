# KID0001 - Prefixes, Derivation and derivation reference tables - Commentary

[![hackmd-github-sync-badge](https://hackmd.io/QBp-0nvKTq2CC7KYkmrBaw/badge)](https://hackmd.io/QBp-0nvKTq2CC7KYkmrBaw)




## Navigation

[Back to table of contents](readme.md)
|Link|Commentary|Section
|---|---|---|
|[0000](kid0000.md)|[X](kid0000Comment.md)|Glossary, overview, how to use|
|[0001](kid0001.md)|X|Prefixes, Derivation and derivation reference tables|
|[0002](kid0002.md)|[X](kid0002Comment.md)|Data model (field & event concepts and semantics)|
|[0003](kid0003.md)|[X](kid0003Comment.md)|Serialization|
|[0004](kid0004.md)|[X](kid0004Comment.md)|Key Configuration (Signing threshold & key set)|
|[0005](kid0005.md)|[X](kid0005Comment.md)|Next Key Commitment (Pre-Rotation)|
|[0006](kid0006.md)|[X](kid0006Comment.md)|Seals|
|[0007](kid0007.md)|[X](kid0007Comment.md)|Delegation (pending PR by Sam)|
|[0008](kid0008.md)|[X](kid0008Comment.md)|Key-Event State Machine|
|[0009](kid0009.md)|[X](kid0009Comment.md)|Indirect Mode & Witnesses|
|0010||Recovery/consensus Algorithm (KAACE)|
|0010||Database & Storage Considerations|
|0097|n/a|**Non-Normative** Implementation Guidance|
|0098|n/a|Use Cases|
|0099|n/a|Test Vectors and Normative Statement Index|

## Editorial Notes
   - KID0001 - Prefixes, Derivation and derivation reference tables (**Seth**)
        * explanation of SCIDs and derivation logic
        * Indexing & Ordering (high-level)
        * Cryptographic Agility & Digest Agility
   * KID0001Comment 
        * Commentary: qualified cryptographic material sections of whitepaper
        * Rationale for complexity necessary to support Digest Agility (as opposed to IPFS and other contemporary systems)
        * Key representation issues {**later PR by Steve**}
            * elliptic curve key compressed representations (TLS bias in most common libraries--> default is uncompressed representation)
            * Signatures in binary handled differently in different crypto libraries

