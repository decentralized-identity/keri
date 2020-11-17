[![hackmd-github-sync-badge](https://hackmd.io/CvQS69NXRxaKu-nDjj1yww/badge)](https://hackmd.io/CvQS69NXRxaKu-nDjj1yww)
## Use Case notes

### KIDs and whitepaper sections

KIDs = sections of a spec? 

Differences between KIDs and RFCs
* Purely chronological versus heirachy
    * Directory structure - allow subtopics & commentary "fork"
    * i.e. 1-datamodel/events.md, 1-datamodel/events-commentary.md, 1-datamodel/state ... 
    * Thomas: Why not a spec tree? One-page diagram showing the dependencies
    * Steve: how do we collect implementation hiccups and discussions to generation from them an implementation FAQ and/or implementers' guide?
        * Sam: PR and Issues --> can be combed/revisited systematically later when an FAQ or guide needs to be written
        * Sam: Pulling out commentary helps-- update commentary in parallel when you merge a PR? 
        * Thomas: TCG documents? - non-normative sidebars as place for [condensed] commentary!
    * Seth: I too have multiple instances open of different implementations and multiple copies of the whitepaper PDF open to different sections... I like the separate files for KIDs while it's in flux!
* Original schema
    * Directory readme?
    * 0 = index (or spec tree?)
        * glossary
        * Steve will take a stab at an overview!
    * 1 = data model & events structure
        * structure
        * types
        * semantics
        * state machine
        * rules
        * ordering
    * 2 = derivation & prefixes
        * tables from whitepaper --> markdown tables
        * SETH VOLUNTEERED I HEARD HIM
    * 3 = serialization
        * CHARLES VOLUNTEERED hehe
    * 4 = state machine?
    * 5 = Direct mode
    * 6 = KAACE & Indirect Mode topography

Additional KIDs needed? Glossary or sidebar for all KID-specific terms?
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
    * glossary

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