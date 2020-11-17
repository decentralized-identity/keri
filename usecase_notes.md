[![hackmd-github-sync-badge](https://hackmd.io/CvQS69NXRxaKu-nDjj1yww/badge)](https://hackmd.io/CvQS69NXRxaKu-nDjj1yww)
## Use Case notes

### KIDs and whitepaper sections

KIDs = sections of a spec? 

Differences between KIDs and RFCs
* Purely chronological versus heirachy
* Original schema
    * 0 = index
    * 1 = data model ...& what events do?
    * 2 = derivation
    * 3 = serialization
    * 4 = state machine?
    * 5 = 

KIDs
* prefixes
* events and state
    * structure
    * types
    * semantics
    * state machine
    * rules
    * ordering
* direct mode
* indirect mode
    * validators
    * witnesses
* split out event structure and contents and versioning from KID3?
    * focusing on serialization
* key config next creation
    * secure multi-party key distribution
* delegation
* Recovery/consensus Algorithm (KAACE)
* Transport details
* Database
* Extracting an event from an HTTP header
* implementation guidance
    * non-normative appendix on test scripts?
    * known/reviewed implementations


### Supply Chain discussion at Decentralized Semantic WG (ToIP) - 10/Nov/20 (Readout from Robert's notes)

- Sidebar: Active / Passive terminology
    - Hashes = passive
    - Transferrable and non-transferable or rotatable/fixed = active any which way (because can sign/interactive proof)
    - Explanation of Passive/Active identifier: https://wiki.trustoverip.org/display/HOME/Passive+Identifiers
- Overall reaction of group:
    - blockchain-savvy crowd excited about entirely offchain/multi-chain sysems
- Different supply chain usecases
    - Robert's pet topic: ""**Cold** chains" (IOT monitoring temperature conditions along transport)
- Benefits slide:
    - "Feedback loop on every step of the chain" - bad outcome at the end, can you pin down where the chain broke down?
    - Minimizing counterfeiting and fraud
    - ePI use case- why can't blockchain?
        - lack of interop/ power struggles
        - problem w/governance framework- who polices admission
        - scaling and privacy
- Microledger approach diagram
    - no network, no blockchain
    - cold chain use case
    - me: everything is offchain and discovery is out-of-band?
    - Sam: DID for everything data provenance [section](https://github.com/WebOfTrustInfo/rwot7-toronto/blob/master/final-documents/A_DID_for_everything.md#data-provenance)
- Sam: ToIP chained VC semantics work?
    - sourcing provenance is one need met by a chain of VCs
    - authorization and consent semantics
        - delegation chains, etc...
        - audit chain, provenance chain, trust/credence chain
    - Charles: machine-readable governance spec or RFC? relevant?
        - Sam: Yes, but that was written by Daniel Hardman, and is just one subset of this world, which needs a broader semantic framework first ; thus renamed 
    - Charles: We are in ESSIF-LAB Infra, and one project there is VC-auth with chained creds...
        - Sam: I'm not sure OCaps/ZCaps work for all use cases, but generic authorization hard to authorize (beyond OS automation, which is its original use case)
        - Charles: that's why we went SGL-based rather than OCap
        - Sam: I need authZ standards
        - Charles: We've experienced a spec gap
- Q&A about use cases
    - Thomas: what's the mechanism for cross-chain navigation or addressing? How do you prefix identifiers to warn you you're jumping chains or KERI networks?
        - Sam: Indy multi-chain case 
        - KERI prefix versus DID namespace fragment (:sov:/:ethr:/etc)
        - canonical...
- 