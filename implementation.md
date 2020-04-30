# Implementation Notes for KERI

https://github.com/decentralized-identity/keri

https://github.com/decentralized-identity/keri/blob/master/implementation.md

https://github.com/SmithSamuelM/keri

https://hackmd.io/orhyiJkLT721v4PCPkvQiA?both

https://github.com/SmithSamuelM/keri/blob/master/implementation.md

smith.samuel.m@gmail.com

https://github.com/SmithSamuelM/Papers/blob/master/whitepapers/KERI_WP_2.x.web.pdf

https://github.com/SmithSamuelM/Papers/blob/master/presentations/KERI2_Overview_IIW_2020_A.pdf




## Things ToDo

1) data element format:
    Anchors hash links not data format. Keep KERI pure (qua standard, and the logs it produces)
    Only define tags in KERI
    
    Tags:  
      a) delegate: KERI delegated identifier prefix
      b) diddoc:  did doc update?
      c) vc:  verifiable credential (issuance, revocation)
    
    Discussion notes:
    - Mitwicki (HCF): we use VCs this way, to contain a minimal payload (hashlink). secure data storage or more public data hubs can be linked this way.
        - Sam: not just hashlink but an identifier that has to be dereferenced 
        - Robert: We're using Manu's hashlinks (DRI) because it contains its own crypto suite etc, but we're a little worried that it exposes these logs to some kinds of correlation attacks.
        - Nader: Here's the reference for that hashlink standard https://tools.ietf.org/html/draft-sporny-hashlink-04
        - Sam: Tag-dependent level of correlatability/lock-in to one encoding or dereferencing dependency
        - Robert: [In our usage of VCs?], we have been thinking about the discovery mechanism via DID Resolution (going from DID to DID:Doc to Service Endpoint [to agent and thus to vault/storage and returned resource]
    - 	Sam: Payloads should be encoding agnostic, mixing and matching should work This is because KERI only cares about the anchor/digest format. The anchored data is not transported in the KERI event so the anchored data can be any encoding.
    - 	
    - 	Mark L Smartopia: Kantara Initiative has been working on consent receipts along these lines, and standardizing on these [essentially legal] events across ontologies has been difficult; we're been able to standardize this and present it at ISO. A consent state record would be a notification and a receipt, and I think this could line up well; we have a GDPR delegation (in close dialogue w/w3c data privacy WG on ontology for this). In the last year, lots of standards have been completed and we're working towards a common record format (legally required to be open).
        - 	Sam: anchor/tag structure and tag-specific link out to data works with your logging needs?
        - 	Sam: a parser needs to know what is anchored by the anchor and how to consume/interpret the digest; the "tag name" is just for a KERI-level categorization of event types
        - 	Mark: we think of delegation as tripartite: regulator, subject, authority; our main data object is also tripartite: notice (event), notification (intermediary), receipt (record)
        - 	Sam: I think you might be imposing semantics from a similar but different definition of authority; I am trying to keep this super agnostic (and specifically about control authority events); 
        - 	Mark: Notary/notification ledger: legal notary + SSI-based ledger; 
        - 	Sam: is KERI preventing you from using KERI in this way? Is this a use-case and can KERI be used without adding anything to it? 
            - 	documentable as a use case for accompanying documentation? **TODO ITEM?**
        - 	Mark: 
        - 	Michael Gorlick: Digest format bears a resemblance to something I worked on IPFS
        - 	Sam: not coincidental! Based on that precedent
        - 	Mark: See also https://www.oasis-open.org/committees/tc_home.php?wg_abbrev=coel
        - 	Nader: See also https://github.com/ipld/specs/blob/master/block-layer/content-addressable-archives.md for IPLD assembling hashes into a digest

 
    - 	Robert: Payload <----> tag relationship (discoverable semantics?) 
        - 	Sam: But I'm afraid that puts the cart in front of the horse and creates a dependency; I want the tag to define the form of the digest, but I want to indirect AWAY from that and force the semantics out to the reference; this is the secure overlay for the internet, not everybody's data format 
        - 	Charles: arbitrary data gets us away from minimal sufficiency
        - 	Sam: Just anchors, that's what i'm calling minimmaly sufficient, spec should not dictate anything about what is anchored, no ontological or semantic conditions or restraints
    - 	Robert: digest prefix ?
    - 	Sam: These list of these tags relates to the DID core spec registry of did doc properties; KERI only cares about the prefixes and assumes a namespaces of self-certifying identifiers (not just DIDs); KERI needs to be a secure spanning layer for identifiers that needs to be manually agnostic to secure events happening in specific namespaces/resolution spaces; 
    - stateless services and self-certifying identifiers
    - 	example: a self-certifying did wrapped in a keri DID:Un
```
did:un:AVrTkep6H-Qt27fThWoNZsa884HA8tr54sHON1vWl6FE/path?kkey=me#flab
```


2)  Version format
    Encoding formats: Json, MsgPack, CBOR, Binary
    
    - JSON vs JSON-LD: data referenced by the payload digest could be -LD; 
    - Robert: what's the idea of the representation of the version?
        - Sam: in my earlier protocol RAET, I used a short string prefix to mark the digest as JSON, MsgPack, Text, or Binary (//Unicode prefix); version-string should bear a prefix (even if redundant from context) in its first few bytes; 
        - Robert: Sam: MsgPack and CBOR are versioned, while JSON isnt, so this
        `- KERI 1.0.0 MsgPack 1.0`
        - Robert: MIME type? Sam: I'm open to it, MIME types don't take up that many bytes...
            - Charles: Restricting the MIME types to a specific subset would help; Sam: yup, each version of KERI should only support a finite list of MIME types (so that it doesn't need to be encoded in each event)
                - examples  `application/keri+json`, `application/keri+binary`



3)  Derivation codes
    Context plus code
    
    prefix
    digest of prev event
    public keys in array
    Next digest (threshold, public key array)
    delegation digests
    by tag data digests data anchor digests
    witnesses prefixes
    signatures
    
    
    Other codes
    
   
4) Languages: Python, Javascript (nodejs), Rust, Python +rust
    keripy, kerijs, keriox,

    Discussion:
    - Sam: Py
    - Spherity (hi!): nodeJS
    - Rust? JOLOCOM ftw (or at least Charles) "KeriOX"

5) Derivation Extraction Library

    - library needs to turn each event into a digest
    - identifier derivated (base64) - non-inception: cyphersuite of public key; inception: need that data; 

    - tag data digest function probably requires a separate library (anchor sublibrary for each tag?)

6) Verification Engine

    - inception event populates state machine
    - derive crypto material, verify it all
    - each new event, derive material, update state
    - the more efficient the better to scale
        - witness validator controller, everyone runs this all the time
    - Charles: replaying key events (and checking the outcome?) --> authoritative key material at any given time
        - Charles: historical DID Document checking?

8) Database for KERLs: LMDB

    - Standardize on LMDB for v1 at least
        - used by (and hardened by) LDAP
        - LDAP license (//BSD + (C)) - pretty free
        - well-coded paragon implementations in every language
        - useful for recovery --> can have multiple entries for each key (appendonly allowing double-entries for forks if you use sequence numbers properly)

    https://github.com/LMDB/lmdb
    
    https://symas.com/lmdb/

8) Controller, Validator, Witness, Watcher, Juror, Judge
9) Clients: web, cmd, python, etc

10) KERI DID method: DID:UN-method (universal but also undoer and destroyer of worlds)

    - Charles: un-conference friendly!


11) Delegation Permissions
    What sort of stuff do we need to permission?
    Nested delegation of new delegated identifiers?
    Delegation of only some data tags?

## Collaboration

COLLAB LOGISTICS: SEE KERI GITHUB REPO on DIF
- attend ID & Discovery meetings of DIF!
- Next Meeting May 11, 2020 11 a.m. PDT
- https://zoom.us/j/801382311
- 
- 

## Old Notes
KERI JS Scope

Event Streaming
Microservices Architecture
Serverless compatible

Each role is a different microservice

Common is core KERI engine

Database LMDB


Start with online case pairwise case

Controller and Validator



## Events

### Inception

![](https://i.imgur.com/foTO32t.png)


```json
{
  "version": "KERI 0.0.1",
  "prefix": "AXq5YqaL6L48pf0fu7IUhL0JRaU2_RxFP0AL43wYn148",
  "sn": 0,
  "ilk": "icp",
  "digest": "EGEj6YfRWmGViKAesa08UkNWukUkPGsdFPPboBAsjRBw",
  "threshold": 2,
  "signers": 
  [
    "AWoNZsa88VrTkep6HQt27fTh-4HA8tr54sHON1vWl6FE",
    "A8tr54sHON1vWVrTkep6H-4HAl6FEQt27fThWoNZsa88",
    "AVrTkep6HHA8tr54sHON1Qt27fThWoNZsa88-4vWl6FE"
  ],
  "next": "EWoNZsa88VrTkep6HQt27fTh-4HA8tr54sHON1vWl6FE",
  "tally": 2,
  "witnesses": 
  [
    "AVrTkep6H-Qt27fThWoNZsa884HA8tr54sHON1vWl6FE",
    "AHON1vWl6FEQt27fThWoNZsa88VrTkep6H-4HA8tr54s",
    "AThWoNZsa88VrTkeQt27fp6H-4HA8tr54sHON1vWl6FE",
  ],
  "data": [],
  "signatures": [0,1]
}
\r\n\r\n
"0AAeYbsHot0pmdWAcgTo5sD8iAuSQAfnH5U6wiIGpVNJQQoYKBYrPPxAoIc1i5SHCIDS8KFFgf8i0tDq8XGizaCg"
\r\n\r\n
"0AHot0pmdWAcgTo5sKFFgf8i0tDq8XGizaCgAeYbsD8iAuSQAfnH5U6wiIGpVNJQQoYKBYrPPxAoIc1i5SHCIDS8"
```

### Rotation

![](https://i.imgur.com/X38o6Kv.png)


```json
{
  "version": "KERI 0.0.1",
  "prefix": "AXq5YqaL6L48pf0fu7IUhL0JRaU2_RxFP0AL43wYn148",
  "sn": 1,
  "ilk": "rot",
  "digest": "GEj6YfRWmGViKAesa08UkNWukUkPGsdFPPboBAsjRBw=",
  "threshold": 2,
  "signers": 
  [
    "AWoNZsa88VrTkep6HQt27fTh-4HA8tr54sHON1vWl6FE",
    "A8tr54sHON1vWVrTkep6H-4HAl6FEQt27fThWoNZsa88",
    "AVrTkep6HHA8tr54sHON1Qt27fThWoNZsa88-4vWl6FE"
  ],
  "next": "EWoNZsa88VrTkep6HQt27fTh-4HA8tr54sHON1vWl6FE",
  "tally": 2,
  "prune": 
  [
    "AVrTkep6H-Qt27fThWoNZsa884HA8tr54sHON1vWl6FE",
  ],
  "graft": 
  [
    "AHA8tr54sHON1vWl6FEVrTkep6H-Qt27fThWoNZsa884",
  ],
  "data": [],
  "signatures": [0,2]
}
\r\n\r\n
"0AAeYbsHot0pmdWAcgTo5sD8iAuSQAfnH5U6wiIGpVNJQQoYKBYrPPxAoIc1i5SHCIDS8KFFgf8i0tDq8XGizaCg"
\r\n\r\n
"0AKFFgf8i0tDq8XGizaCgAeYbsHot0pmdWAcgTo5sD8iAuSQAfnH5U6wiIGpVNJQQoYKBYrPPxAoIc1i5SHCIDS8"
```

### Interaction

![](https://i.imgur.com/vr7oyg5.png)


```json
{
  "verison": "KERI 0.0.1",
  "prefix": "AXq5YqaL6L48pf0fu7IUhL0JRaU2_RxFP0AL43wYn148",
  "sn": 2,
  "ilk": "ixn",
  "digest": "GEj6YfRWmGViKAesa08UkNWukUkPGsdFPPboBAsjRBw=",
  "threshold": 2,
  "signers": 
  [
    "AWoNZsa88VrTkep6HQt27fTh-4HA8tr54sHON1vWl6FE",
    "A8tr54sHON1vWVrTkep6H-4HAl6FEQt27fThWoNZsa88",
    "AVrTkep6HHA8tr54sHON1Qt27fThWoNZsa88-4vWl6FE"
  ],
  "data": [],
  "signatures": [0,2]
}
\r\n\r\n
"0AAeYbsHot0pmdWAcgTo5sD8iAuSQAfnH5U6wiIGpVNJQQoYKBYrPPxAoIc1i5SHCIDS8KFFgf8i0tDq8XGizaCg"
\r\n\r\n
"0AKFFgf8i0tDq8XGizaCgAeYbsHot0pmdWAcgTo5sD8iAuSQAfnH5U6wiIGpVNJQQoYKBYrPPxAoIc1i5SHCIDS8"
```

### Data

#### Delegate Tag
```json

"data":
[
  {
    "delegate": 
    {
      "prefix": "AXq5YqaL6L48pf0fu7IUhL0JRaU2_RxFP0AL43wYn148",
      "sn": 0,
      "digest": "GEj6YfRWmGViKAesa08UkNWukUkPGsdFPPboBAsjRBw"
    }
  },
  {
    "delegate": 
    {
      "prefix": "AY25YqaL6L48pf0fu7IUhL0JRaU2_RxFP0AL43wYn139",
      "sn": 0,
      "digest": "GFj6YfRWmGViKAesa08UkNWukUkPGsdFPPboBAsjRBw"
    }
  }
]
```

### Delegation

![](https://i.imgur.com/QzBtfnb.png)



#### Delegating Interaction

![](https://i.imgur.com/bNrHhsu.png)

```json
{
  "verison": "KERI 0.0.1",
  "prefix": "AXq5YqaL6L48pf0fu7IUhL0JRaU2_RxFP0AL43wYn148",
  "sn": 2,
  "ilk": "ixn",
  "digest": "GEj6YfRWmGViKAesa08UkNWukUkPGsdFPPboBAsjRBw=",
  "threshold": 2,
  "signers": 
  [
    "AWoNZsa88VrTkep6HQt27fTh-4HA8tr54sHON1vWl6FE",
    "A8tr54sHON1vWVrTkep6H-4HAl6FEQt27fThWoNZsa88",
    "AVrTkep6HHA8tr54sHON1Qt27fThWoNZsa88-4vWl6FE"
  ],
  "data": 
  [
    {
      "delegate": 
      {
        "prefix": "AXq5YqaL6L48pf0fu7IUhL0JRaU2_RxFP0AL43wYn148",
        "sn": 0,
        "digest": "GEj6YfRWmGViKAesa08UkNWukUkPGsdFPPboBAsjRBw"
      }
    }
  ],
  "signatures": [0,2]
}
\r\n\r\n
"0AAeYbsHot0pmdWAcgTo5sD8iAuSQAfnH5U6wiIGpVNJQQoYKBYrPPxAoIc1i5SHCIDS8KFFgf8i0tDq8XGizaCg"
\r\n\r\n
"0AKFFgf8i0tDq8XGizaCgAeYbsHot0pmdWAcgTo5sD8iAuSQAfnH5U6wiIGpVNJQQoYKBYrPPxAoIc1i5SHCIDS8"
```

#### Delegating Rotation



![](https://i.imgur.com/mipTTUr.png)


```json
{
  "version": "KERI 0.0.1",
  "prefix": "AXq5YqaL6L48pf0fu7IUhL0JRaU2_RxFP0AL43wYn148",
  "sn": 1,
  "ilk": "rot",
  "digest": "GEj6YfRWmGViKAesa08UkNWukUkPGsdFPPboBAsjRBw=",
  "threshold": 2,
  "signers": 
  [
    "AWoNZsa88VrTkep6HQt27fTh-4HA8tr54sHON1vWl6FE",
    "A8tr54sHON1vWVrTkep6H-4HAl6FEQt27fThWoNZsa88",
    "AVrTkep6HHA8tr54sHON1Qt27fThWoNZsa88-4vWl6FE"
  ],
  "next": "EWoNZsa88VrTkep6HQt27fTh-4HA8tr54sHON1vWl6FE",
  "tally": 2,
  "prune": 
  [
    "AVrTkep6H-Qt27fThWoNZsa884HA8tr54sHON1vWl6FE",
  ],
  "graft": 
  [
    "AHA8tr54sHON1vWl6FEVrTkep6H-Qt27fThWoNZsa884",
  ],
  "data": 
  [
    {
      "delegate": 
      {
        "prefix": "AXq5YqaL6L48pf0fu7IUhL0JRaU2_RxFP0AL43wYn148",
        "sn": 0,
        "digest": "GEj6YfRWmGViKAesa08UkNWukUkPGsdFPPboBAsjRBw"
      }
    }
  ],
  "signatures": [0,2]
}
\r\n\r\n
"0AAeYbsHot0pmdWAcgTo5sD8iAuSQAfnH5U6wiIGpVNJQQoYKBYrPPxAoIc1i5SHCIDS8KFFgf8i0tDq8XGizaCg"
\r\n\r\n
"0AKFFgf8i0tDq8XGizaCgAeYbsHot0pmdWAcgTo5sD8iAuSQAfnH5U6wiIGpVNJQQoYKBYrPPxAoIc1i5SHCIDS8"
```



### Delegated Inception

![](https://i.imgur.com/EaKLgLW.png)

![](https://i.imgur.com/JiAyeH5.png)


```json
{
  "version": "KERI 0.0.1",
  "prefix": "AXq5YqaL6L48pf0fu7IUhL0JRaU2_RxFP0AL43wYn148",
  "sn": 0,
  "ilk": "dip",
  "digest": "EGEj6YfRWmGViKAesa08UkNWukUkPGsdFPPboBAsjRBw",
  "threshold": 2,
  "signers": 
  [
    "AWoNZsa88VrTkep6HQt27fTh-4HA8tr54sHON1vWl6FE",
    "A8tr54sHON1vWVrTkep6H-4HAl6FEQt27fThWoNZsa88",
    "AVrTkep6HHA8tr54sHON1Qt27fThWoNZsa88-4vWl6FE"
  ],
  "next": "EWoNZsa88VrTkep6HQt27fTh-4HA8tr54sHON1vWl6FE",
  "tally": 2,
  "witnesses": 
  [
    "AVrTkep6H-Qt27fThWoNZsa884HA8tr54sHON1vWl6FE",
    "AHON1vWl6FEQt27fThWoNZsa88VrTkep6H-4HA8tr54s",
    "AThWoNZsa88VrTkeQt27fp6H-4HA8tr54sHON1vWl6FE",
  ],
  "data": 
  [
    {
      "delegate": 
      {
        "prefix": "AXq5YqaL6L48pf0fu7IUhL0JRaU2_RxFP0AL43wYn148",
        "sn": 0,
        "digest": "GEj6YfRWmGViKAesa08UkNWukUkPGsdFPPboBAsjRBw"
      }
    }
  ],
  "signatures": [0,1]
}
\r\n\r\n
"0AAeYbsHot0pmdWAcgTo5sD8iAuSQAfnH5U6wiIGpVNJQQoYKBYrPPxAoIc1i5SHCIDS8KFFgf8i0tDq8XGizaCg"
\r\n\r\n
"0AHot0pmdWAcgTo5sKFFgf8i0tDq8XGizaCgAeYbsD8iAuSQAfnH5U6wiIGpVNJQQoYKBYrPPxAoIc1i5SHCIDS8"
```

### Delegated Rotation

![](https://i.imgur.com/3T4h8Pu.png)

![](https://i.imgur.com/81nzRTt.png)


```json
{
  "version": "KERI 0.0.1",
  "prefix": "AXq5YqaL6L48pf0fu7IUhL0JRaU2_RxFP0AL43wYn148",
  "sn": 1,
  "ilk": "rot",
  "digest": "GEj6YfRWmGViKAesa08UkNWukUkPGsdFPPboBAsjRBw=",
  "threshold": 2,
  "signers": 
  [
    "AWoNZsa88VrTkep6HQt27fTh-4HA8tr54sHON1vWl6FE",
    "A8tr54sHON1vWVrTkep6H-4HAl6FEQt27fThWoNZsa88",
    "AVrTkep6HHA8tr54sHON1Qt27fThWoNZsa88-4vWl6FE"
  ],
  "next": "EWoNZsa88VrTkep6HQt27fTh-4HA8tr54sHON1vWl6FE",
  "tally": 2,
  "prune": 
  [
    "AVrTkep6H-Qt27fThWoNZsa884HA8tr54sHON1vWl6FE",
  ],
  "graft": 
  [
    "AHA8tr54sHON1vWl6FEVrTkep6H-Qt27fThWoNZsa884",
  ],
  "data": 
  [
    {
      "delegate": 
      {
        "prefix": "AXq5YqaL6L48pf0fu7IUhL0JRaU2_RxFP0AL43wYn148",
        "sn": 0,
        "digest": "GEj6YfRWmGViKAesa08UkNWukUkPGsdFPPboBAsjRBw"
      }
    }
  ],
  "signatures": [0,2]
}
\r\n\r\n
"0AAeYbsHot0pmdWAcgTo5sD8iAuSQAfnH5U6wiIGpVNJQQoYKBYrPPxAoIc1i5SHCIDS8KFFgf8i0tDq8XGizaCg"
\r\n\r\n
"0AKFFgf8i0tDq8XGizaCgAeYbsHot0pmdWAcgTo5sD8iAuSQAfnH5U6wiIGpVNJQQoYKBYrPPxAoIc1i5SHCIDS8"
```


### Delegated Interaction


![](https://i.imgur.com/U3uqrZh.png)


```json
{
  "verison": "KERI 0.0.1",
  "prefix": "AXq5YqaL6L48pf0fu7IUhL0JRaU2_RxFP0AL43wYn148",
  "sn": 2,
  "ilk": "ixn",
  "digest": "GEj6YfRWmGViKAesa08UkNWukUkPGsdFPPboBAsjRBw=",
  "threshold": 2,
  "signers": 
  [
    "AWoNZsa88VrTkep6HQt27fTh-4HA8tr54sHON1vWl6FE",
    "A8tr54sHON1vWVrTkep6H-4HAl6FEQt27fThWoNZsa88",
    "AVrTkep6HHA8tr54sHON1Qt27fThWoNZsa88-4vWl6FE"
  ],
  "data": [],
  "signatures": [0,2]
}
\r\n\r\n
"0AAeYbsHot0pmdWAcgTo5sD8iAuSQAfnH5U6wiIGpVNJQQoYKBYrPPxAoIc1i5SHCIDS8KFFgf8i0tDq8XGizaCg"
\r\n\r\n
"0AKFFgf8i0tDq8XGizaCgAeYbsHot0pmdWAcgTo5sD8iAuSQAfnH5U6wiIGpVNJQQoYKBYrPPxAoIc1i5SHCIDS8"
```