# KID0000 - Glossary, overview, how to use - Commentary


## Navigation

[Back to table of contents](readme.md)
|Link|Commentary|Section
|---|---|---|
|[0000](kid0000.md)|X|Glossary, overview, how to use|
|[0001](kid0001.md)|[X](kid0001Comment.md)|Prefixes, Derivation and derivation reference tables|
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
- jan 5 notes
    - KID0000 - Glossary, overview, how to use {**Leave for later**}
        - High-Level overview of Operating Modes (Direct, Indirect, Ephemeral)
        - Dainty and Narrow Scope
            - Dependency/RFC List (the thorax between the KERI neck and the IP waist): base64, messagePack, CBOR & JSON, ECC Dig Sigs, [128+] Cr. Digests, Messaging: UDP/TCP/HTTP (for now), standard HEX alphabet RFC
            - {Note to self: review [this](https://github.com/decentralized-identity/keri/issues/82)}
            - Implementation guide: explanation of higher-level behavior assumptions codified into test suites
    - KID0000Comment - Mental models & big-picture rationale
        * Intro to SCIDs? (Whitepaper 2.3)
            * {Include link to Unified Identifier whitepaper}
        * Cryptographic Trust Basis (Whitepaper 2.4)
        * Autonomic Namespace (Whitepaper 3.1) & Syntax (3.2)
        * Unified Identifier Model (3.3)
        * KERI "Layering" and Scope
            * Explanation of VCs, VC-Auth/Capabilities, etc.
            * Out of scope but useful if specified: Assumptions one layer up
                * link to Authentic Chained Data Container spec at ToIP

