# Implementation Notes for KERI

https://github.com/decentralized-identity/keri

https://github.com/decentralized-identity/keri/blob/master/implementation.md

https://github.com/SmithSamuelM/keri

https://hackmd.io/orhyiJkLT721v4PCPkvQiA?both

https://github.com/SmithSamuelM/keri/blob/master/implementation.md


## Things ToDo

1) data element format:
    Anchors hash links not data format. Keep KERI pure
    Only define tags in KERI
    
    Tags:  delegate
    
2)  Version format
    Encoding formats: Json, MsgPack, CBOR, Binary

3)  Version codes
    Context plus code
    
    prefix
    digest of prev event
    public keys
    delegation digests
    witnesses
    signatures
    data anchor digests
    
    Other codes
    
4) Languages: Python, Javascript (nodejs), Rust, Python +rust
    keripy, kerijs, keriox,

5) Derivation Extraction Library

6) Verification Engine
7) Database for KERLs: LMDB

    https://github.com/LMDB/lmdb
    
    https://symas.com/lmdb/

8) Controller, Validator, Witness, Watcher, Juror, Judge
9) Clients: web, cmd, python, etc


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
  "verison": "KERI 0.0.1",
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
  "verison": "KERI 0.0.1",
  "prefix": "AXq5YqaL6L48pf0fu7IUhL0JRaU2_RxFP0AL43wYn148",
  "sn": 1,
  "ilk": "rot",
  "digest": "GEj6YfRWmGViKAesa08UkNWukUkPGsdFPPboBAsjRBw=",
  "threshold": 2,
  "signers": 
  [
    "AWoNZsa88VrTkep6HQt27fTh-4HA8tr54sHON1vWl6FE=",
    "A8tr54sHON1vWVrTkep6H-4HAl6FEQt27fThWoNZsa88=",
    "AVrTkep6HHA8tr54sHON1Qt27fThWoNZsa88-4vWl6FE="
  ],
  "next": "EWoNZsa88VrTkep6HQt27fTh-4HA8tr54sHON1vWl6FE",
  "tally": 2,
  "prune": 
  [
    "VrTkep6H-Qt27fThWoNZsa884HA8tr54sHON1vWl6FE=",
  ],
  "graft": 
  [
    "HA8tr54sHON1vWl6FEVrTkep6H-Qt27fThWoNZsa884=",
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
  "ilk": "icx",
  "digest": "GEj6YfRWmGViKAesa08UkNWukUkPGsdFPPboBAsjRBw=",
  "threshold": 2,
  "signers": 
  [
    "AWoNZsa88VrTkep6HQt27fTh-4HA8tr54sHON1vWl6FE=",
    "A8tr54sHON1vWVrTkep6H-4HAl6FEQt27fThWoNZsa88=",
    "AVrTkep6HHA8tr54sHON1Qt27fThWoNZsa88-4vWl6FE="
  ],
  "data": [],
  "signatures": [0,2]
}
\r\n\r\n
"0AAeYbsHot0pmdWAcgTo5sD8iAuSQAfnH5U6wiIGpVNJQQoYKBYrPPxAoIc1i5SHCIDS8KFFgf8i0tDq8XGizaCg"
\r\n\r\n
"0AKFFgf8i0tDq8XGizaCgAeYbsHot0pmdWAcgTo5sD8iAuSQAfnH5U6wiIGpVNJQQoYKBYrPPxAoIc1i5SHCIDS8"
```

### Delegation


### Delegated Inception


### Delegated Rotation


