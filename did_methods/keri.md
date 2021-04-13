# `did:keri` Method Spec

## Introduction
KERI provides a means for secure and decentralised key management. This specification defines a DID method based on KERI.

## Concepts
The Key Event Receipt Infrastructure is a system for secure self-certifying Identifiers which aims at minimum sufficiency and maximum security. It defines mechanisms for proving the Root of Trust for self-certifying Identifiers and their associated Key State. This spec defines a transform from Key State to DID Document, such that any valid Key Event Log can be processed into a DID Document.

A close analogy is [`did:peer`](https://identity.foundation/peer-did-method-spec/), except that where the data model of `did:peer` is a DID Document and JSON patches on said Document, the basic data model of `did:keri` is an append-only log of Key Events. KERI-based Identifiers are suitable for both any-wise and n-wise purposes.

### Key State
A Key State is a mapping of an identifier to a set of public keys:
`Id => PubKey[]`

Additionally, delegating Identifiers allow an extra mapping between Identifier (itself) and a set of one or more Delegated identifiers ('children'):
`Id => Id[]`

Each delegated identifier has a mapping back to its delegating identifier ('parent').

### Events
A Key Event is an atomic transaction over the Key State of an Identifier. While all events have some semantic meaning within KERI, only a subset will change the keys in a Key State (rotation and delegated rotation).

### Key Event Log
The Key Event Log is a type of hash-chained data structure from which the Key State of an Identifier can be derived. It can always be used to recreate the state at any point ("event-sourcing").


### Key Event Receipt Log
The Key Event Receipt Logs are built from receipts of events signed by the witnesses of those events (these are called '**commitments**'); these are also append-only but not hash-chained.

### Message types
* Event State Messages - tbd
* Receipt Messages - tbd
* Event Messages - tbd

### Witness Identifiers & Delegation
tbd

### Prefix
tbd
* question: link to prefix table in KERI spec?

### Resolver Metadata
* MUST have everything necessary to prove control
* Open question: Should it signal in the metadata that it's an UN-DID to distinguish it from a minimalist DID in another method containing the same set of metadata?

### The DID document
Optionally, a public key could be the only thing in the DID Doc (for interop with other W3C DID components and systems). Technically, it could be empty if only being used to prove DID control.

* Open question: should this spec be opinionated about extra info in DID:Doc (say, service endpoints)

Non-normative note: multiple namespaces using the same DID method could prove control or replay history for one controlling keypair that has been used across multiple ledgers. KERL logs could be stored in a secondary root of trust (i.e., a ledger), and similar or identical resolver metadata could be returned by querying the same identifier there.  

### DID Discovery

Sam: I'm imagining DHT tables of zone files (//DNS CNAMEs). Witness names could resolve to zone files, which could in turn contain routing info/addresses. If you have a log and need to find witnesses to further validate, some layer/mechanism would need to sit on top. (Sidenote: grad stude at BYU working on a Kademlia mechanism to sidestep DNS et al.) Ideally, starting from a hashed inception event and one witness to get a full log.

Resolution results could return, along with did doc and meta data, service endpoints (following the school of thought that wants to deliver VCs with service endpoints along with rather than inside of DID Docs). DID-CORE LIMBO BLAARGH

## Specification

### Create
Creation of a `did:keri` DID is accomplished by creating an Inception event. If witnesses are listed in the inception event, the receipts are also required for DID creation to be complete.

### Read
Steps to resolve a `did:keri:$PREF` DID:
1. Find the Key Event Log for the prefix `$PREF` (is this step outside the scope of this spec? KERI provides no cannonical availability mechanism, but one could be chosen for a particular DID method spec by the spec writers (witnesses could work for this))
2. Process the KEL into a Key State, according to the state validation rules/semantics of KERI (out of scope probably)
3. Create a DID Document with the DID `did:keri:$PREF`
4. For each key K in the Key State, add a Verification Method to the DID Doc containing K and the appropriate type, with the ID of K being K's prefix form (alternatively, the ID could be an integer of K's index in the current signer list)

Establishment of control authority can be done independantly of DID document contents, as long as the KERL is provided in the resolver metadata.

Optional Steps:

5. For each witness of `$PREF`, add a service endpoint describing the witness

Questions:
- What about delegated identifiers? options:
    1. Delegated Identifiers are treated as normal identifiers (they use `did:keri:$D_PREF`) with their own DID Doc.
    2. Delegated Identifier DIDs are prepended with the delegators DID (e.g. `did:keri:$PREF#$D_PREF`). This provides a kind of namespacing in DID land
- Each delegated identifier may be listed in the delegators DID Doc as a service endpoint? ownedBy? sameAs?
    - E.g. see https://w3c.github.io/did-core/#alsoknownas and https://github.com/w3c/did-core/issues/421
- Q: Availability opinions or recommendations? Non-normative appendix to be written later?
    - A: Agnosticism and portability better served by being mute here-- controller gets to decide their requirements and how widely to publish or how available to make their events; validators can negotiate as well on their side

### Update

### Delete
Deletion of a `did:keri` DID consists of rotation to 0 controling keys, which terminates the ability to recover the identifier and indicates that the identifier has been abandoned. Identifiers which are delegated to by an abandoned Identifier are also considered abandoned (delegating Ixn events can no longer be created). Document Title

