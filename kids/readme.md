# KIDs overview

|KID|Commentary|Contents|Status|Ownership/primary author|
|---|---|---|---|---|
|[0000](kid0000.md)|[X](kid0000Comment.md)|Glossary, overview, how to use|on hold|henk+juan|
|[0001](kid0001.md)|[X](kid0001Comment.md)|Prefixes, Derivation and derivation reference tables|incoming|seth|
|[0002](kid0002.md)|[X](kid0002Comment.md)|Data model (field & event concepts and semantics)|incoming|tbd|
|[0003](kid0003.md)|[X](kid0003Comment.md)|Serialization|strawman but PRs incoming (sam+charles)|charles|
|[0004](kid0004.md)|[X](kid0004Comment.md)|Key Configuration (Signing threshold & key set)|strawman|michael|
|[0005](kid0005.md)|[X](kid0005Comment.md)|Next Key Commitment (Pre-Rotation)|strawman|juan|
|[0006](kid0006.md)|[X](kid0006Comment.md)|Seals|strawman (pending PR by Sam)|juan|
|[0007](kid0007.md)|[X](kid0007Comment.md)|Delegation (pending PR by Sam)|strawman|juan|
|[0008](kid0008.md)|[X](kid0008Comment.md)|Key-Event State Machine|tbd|tbd|
|[0009](kid0009.md)|[X](kid0009Comment.md)|Indirect Mode & Witnesses|incomplete strawman|tbd|
|0010|Recovery/consensus Algorithm (KAACE)|on hold|tbd|
|0011|Database & Storage Considerations|on hold|tbd
|0097|**Non-Normative** Implementation Guidance|on hold|tbd|
|0098|Use Cases|incoming|(Michael, Robert, Charles, and GLEIF?)|
|0099|Test Vectors and Normative Statement Index|on hold for final editorial review|tbd|

## Further Documentation waiting on stable code development 
- KID0011 - Recovery/consensus Algorithm (KAACE)
    * Roles: Validator, Witness, etc
    * **Normative** API assumptions between all the reference implementations? (Leave for later? Decide how much of this is non-normative after WG-wide discussion :D )
- KID0012 - Databases
    - Right to erasure (see digest agility Issue)
- KID0097 - **Non-Normative** Implementation Guidance
    - Key Creation
    - Key Storage
    - Event Signing
- KID0099 - Test Vectors & Normative Statements
    * Validation table
    * Index of normative statements 

## Out of scope for now (incl. future/separate specs/work items)
- Implementation Details 
    - Storage? Database mechanics specified?
    - Common API
        * KMS API assumptions
    - Discovery (KERI-Dehmlia)
        - GH Issue on delegation mechanics
        - "Layer above KERI" spec - work item for the future?
    - Transport
    - Extracting an event from an HTTP header? appendix?
