# KERI Project Agenda

[![hackmd-github-sync-badge](https://hackmd.io/eBKWws_uRZyq3aOTEKfHlQ/badge)](https://hackmd.io/eBKWws_uRZyq3aOTEKfHlQ)

## Weekly Meeting Page

This page is for agendas and minutes of the weekly KERI-related work-item meetings of the [KERI Working Group](https://identity.foundation/keri/), who are collaborating on topics related to DIDs and other identifiers. Meeting agendas are listed in reverse chronological order. Meetings will be recorded. This is an IPR-protected meeting, so please refrain from making substantial contributions orally on calls or on github before joining both DIF and the WG. You can get more information from the chairs or at [membership@identity.foundation](mailto:membership@identity.foundation). DIF membership info can be found [here](https://link.medium.com/PCtPmbHJV7).

Meeting Time: Every Tuesday, 10 am ET / 8 am MT (see DIF [google calendar](https://bit.ly/dif-calendar))

#### Links: 
[DIF WG Page](https://identity.foundation/working-groups/keri.html)    
[ID WG Charter](https://bit.ly/DIF-WG-select1)  
Slack [channel](https://difdn.slack.com/archives/C0146LH5XQD)  
Github Repos:  core , rust, python, javascript, go, and java (need to add links here)  
Publicity [website](https://keri.one/)   
 A [note](https://tools.ietf.org/id/draft-knodel-terminology-02.html) on nomenclature used in this spec   
 Meeting [Recordings](https://docs.google.com/spreadsheets/d/1wgccmMvIImx30qVE9GhRKWWv3vmL2ZyUauuKx3IfRmA/edit#gid=1393617996) 
 
 ZOOM [ROOM](https://us02web.zoom.us/j/81492837711?pwd=OU01ZVpYYmdrcGJDNHhUWU5VNDkxdz09) Meeting ID: 814 9283 7711 Passcode: 268606
 
## RoadMap



## Future/Pending Topics
- direct-mode interop updates post breaking changes
- non-interactive authentication mechanism for query protocol KRAM (Keri Request Authentication Mechanism)
- [delegator/delegate coordination for delegated events](https://github.com/decentralized-identity/keri/issues/82)
- [use cases document](https://github.com/decentralized-identity/keri/issues/120)
- [Daniel Hardman et al.'s VC attack surface article](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/final-documents/alice-attempts-abuse-verifiable-credential.pdf) - use this to structure a future discussion on KERI-based VC architecture review? Does TELs+VCs offer a defensible architecture?
    - Decentralized reputation systems might still be the key to sealing out the duplicity and realworld misincentives 

## Agenda TEMPLATE (copy and paste)

- Implementors update
    - keripy
    - keriox
    - kerijs
    - kerigo
    - kerijava
    - keridht

- Other topics?

- Issue review
    - [keri main](https://github.com/decentralized-identity/keri/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc)
    - keripy
    - keriox
    - kerijs
    - kerigo
    - kerijava
    - keridht

## Agenda Nov 09

- Implementors update
    - keripy
    - keriox
        - PR for parsing signed reciepts
    - kerijs
    - kerigo
    - kerijava
    - keridht

- Other topics?
    - work item proposals:
        - from slack (Michal), future use cases feasible to work with:
            - blockchainless solutions based on keri architecture principles
            - authentic interactions on microledgers
            - general-purpose TELs
            - "KERI for mortals"
        - From Jolocom
            - did:keri method resolver/spec - ID working group?
                - [current dif spec](https://identity.foundation/keri/did_methods/)
            - general structure of components to bring into a spec eventually
                - continue work on a KERI-achitected (but not necessarily compatible with gleif-keri) spec? yes
        - from discussion
            - proposal to do work elsewhere or depending on ietf work
                - seems reasonable that DIF work can depend on IETF work
                - IETF guarentees patent disclosure on drafts/published items
                    - a draft without disclosed patents is safe
                - several KERI component concepts have already been posted as IETF drafts
                - KERI itself is WIP

- Issue review
    - [keri main](https://github.com/decentralized-identity/keri/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc)
    - keripy
    - keriox
    - kerijs
    - kerigo
    - kerijava
    - keridht

## Agenda Nov 02

- Implementors update
    - keripy
    - keriox
    - kerijs
        - issuance and revocation in VDR (Verifiable Data Registry) model implementation
    - kerigo
    - kerijava
    - keridht

- Other topics?
    - Discuss objections, if any, to last week's proposal
    - work item discussion
        - Propose work items:
            - CESR or CESR-like encoding for cryptographic material
                - [CBB encoding](https://github.com/decentralized-identity/crypto-wg/blob/main/work_items/cbb_data_encoding.md) already accepted by DIF AppCry WG - Steve has taken up editor role there, issues and PRs from this group welcome!
                    - relationship to multicodec... up in the air?
            - compound data representations, events, attachment model, transport representation
                - HCF? Robert's proposal (a month or two ago) to break out pieces organically over time as specifications for them become useful/needed for specific use-cases; relationship to TOIP ACDC group?
                - Steve also working on [CBB protocol](https://github.com/decentralized-identity/crypto-wg/blob/main/work_items/cbb_service_protocol.md)
                - Spruce also working on ["policy as code" CDDL-like thing](https://github.com/decentralized-identity/crypto-wg/blob/main/work_items/cbb_policy_as_code.md)
            - authentic log/microledger structure and validation rules
                - too early maybe? requires the two above?
            - potential use-cases for KERI-like systems beyond identifiers
                - TELs and TEL-like VCs
                - timestamp services, other consensus or witnessing services
        - steve: whats the desired outcome?
            - how similiar to alternative?
            - applied crypto wg would provide tools for generating/analysing the pieces
            - most parties want to be interoperable
        - what does everyone want?
            - interoperability with gleif?
                - what exactly does that mean?
                    - log/event/attachment formats are mutually understandable
                    - transport of log events among participants
                    - overall architecture of actors/roles (witnesses/watchers/controllers)
                - a mirror spec does not resolve any IPR issues

- Issue review
    - [keri main](https://github.com/decentralized-identity/keri/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc)
    - keripy
    - keriox
    - kerijs
    - kerigo
    - kerijava
    - keridht

## Agenda Oct 26

- Implementors update
    - keripy
    - keriox
    - kerijs
        - Shivam (over DM): Currently, I am working with VIR (Verifiable issuance registry) and VDR (Verifiable Data Registry), working on code for handling this locally, will PR when stable
    - kerigo
    - kerijava
    - keridht

- Other topics?
    - Proposal:
        - from last week:
            - define the boundaries of Keri work item IP
                - what goes?
                - Identify a cutoff date for contributions, everything contributed before this date is covered
                    - after that date, close the work item for contributions and open a new work item which can reference the old
                - what is the new work Item, what is proposed
                    - use the existing code bases as reference for new spec development
            - move Keri to a work Item under ID WG or Applied Crypto WG
                - preferences? governance? process?
        - process:
            - community notification
                - send out notification of the proposal to the wider community, allow time for consideration but non-response is non-objection
                    - notification: Hello KERI DIF Community, The KERI working group has discussed a proposal to scale back the scope of the work to a Work Item under another DIF working group[1]. This proposal entails:
                        1 Defining a new working item scope, including existing implementations
                        2 petitioning/accepting the initiation of said new work item into an existing DIF working group
                        3 Archiving the specification activities (and repo) of the KERI working group
                    - Any parties with objections to or suggestions for this proposal are invited to respond to this email (whether only to the chair or replying-all) before the next working group call on Nov 02. Thanks for any input
                        [1] (Notes for these calls can be found here)[https://hackmd.io/eBKWws_uRZyq3aOTEKfHlQ]
                    -  
                - have a github issue for discussion, email out a statement with link
                - charles will send it out
                - next call (02/11) consider objections then assume consensus
            - destination wg consultation
                - consult these WGs to find who is more suitable/amenable
            - Identify a cutoff time to archive the wg and start the work item
            - define the proposed work item focus/goals
                - ivan: off the top of my head, i'd propose some goals for the work item including:
                    - real-world use cases
                    - explanations of how to swap out serialization/encoding for others
                    - using didcomm as a transport
                    - TEL stuff
                    - etc...  
                - implications on implementations hosted on DIF repos
                    - implementations housed under dif are only safe from patent action insofar as they don't take influence from squishy, fluid ideas from outside sources (ratified/published specs incur much less risk)
                    - else be susceptible to potential (currently secret) patent violation claims down the line
                    - end goal of all DIF/JDF processes is a patent-claim-free spec which is safe to use
                        - (parties desiring this should join DIF)

- Issue review
    - [keri main](https://github.com/decentralized-identity/keri/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc)
    - keripy
    - keriox
    - kerijs
    - kerigo
    - kerijava
    - keridht


## Agenda Oct 19

- Implementors update
    - keripy
    - keriox
    - kerijs
    - kerigo
    - kerijava
    - keridht

- Other topics?
    - proposals for next call
        - maintain the existing spec work under dif as a work item in a different group
            - drawing a clean boundary around the IP protected work
            - preferrably also maintain an interop profile to meet
    - Joachim's agenda proposals
        - Legal protection and clean version of DIF-KERI
            - moving the work outside of DIF might compromise it's IPR status/make it vulnerable to patent trolling/other forms of legal attack :(
            - identifying parts of the spec to manage separately could help
            - IETF's IPR policy is not that work items be free of patents, but that those patents are open and non-discriminant
                - so IETF work items can be patented, while those of DIF are protected from patents
            - if any contributor can decide they have patent rights they'd need to exclude, they should declare ASAP
                - has anyone declared that? no, given contributors signing of the DIF membership agreement
                - technically true that you could do that at a late stage
                - it seems that all parties are aligned on KERI being an open, free spec
        - Scale back WG to work item
            - KERI WG is significant overhead
            - Charles the only active co-chair
            - retire WG
        - Define Keri work item moving forward (to-do for us as WG)
        - propose defined Keri work item to either DIF Applied Crypto WG or DIF ID WG (where it actually derived from)
            - microledger spec? AppCry WG already considering a microledger/prov-log item with both KERI and non-KERI members participating
                - Steve: designing a KERI-agnostic, more widely-useful provenance log, looking at both KERI and non-KERI use cases (with Dave Huseby from CryptID); 
                - KERI is not a general method for provenance logs, it has details specific to it's purpose
            - Iván: interop targets? shoot for IETF overarching KERI-profile spec after it's done, to preserve IPR along the way?
            - did:un/did:keri ?

- Issue review
    - [keri main](https://github.com/decentralized-identity/keri/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc)
    - keripy
    - keriox
    - kerijs
    - kerigo
    - kerijava
    - keridht

## Agenda Oct 5

- Implementors update
    - keripy
    - keriox
        - PR #80 merged
    - kerijs
        - testing weighted threshold logic for signatures on events, PR incoming
    - kerigo
    - kerijava
    - keridht

- Other topics?
    - Once work begins at another SDO/venue, what is this groups approach?
        - proposal: contact all wg members and request input/attendance for:
            - where/if to move sub-spec work (applied crypto wg?)
            - where to continue implementation discussion
            - where to continue/source more spec work
        - Robert: actual venue for work is immaterial, orgs would mainly like to continue work, code is a bit more relevant than the spec itself (re: adoption/progress)
            - most parties seem to not mind the IPR situation
            - extraction/expansion of the microledger concept is a valuable outcome, generalises the existing work
            - suggest moving that kind of work (CESR, microledger) to applied-crypto WG
            - Authentic Data concept is of greater impact than specific examples of such e.g. SSI, KERI
            - Not all the parallel KERI work is under ToIP, just the ACDC-relevant sub-specs like CESR
                - the overall KERI work continues under the gleif group
        - Joachim: steering commitee is considering this issue
            - goal is a clean and fair arrangement which allows all parties to continue the work together
        - Robert: not quite an admin issue but a personal one
            - unlikely that any groups will apply for or enforce any patents on KERI
            - implementation work and spec work are not necessarily bound together
        - impl and spec work can proceed independantly (e.g. impls at DIF, spec work at applied crypto wg and/or IETF)
    - DID method rubric podcast
        - will be put in contact with a rep for Joe
    - Robert: there now exists a [microledger implementation](https://github.com/THCLab/microledger)
        - will try to pursue this in SENS: JPC-19

- Issue review
    - [keri main](https://github.com/decentralized-identity/keri/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc)
    - keripy
    - keriox
    - kerijs
    - kerigo
    - kerijava
    - keridht

## Agenda Sept 28

- Implementors update
    - keripy
    - keriox
        - [PR #80](https://github.com/decentralized-identity/keriox/pull/80): Delegation update to implement hetero attachments and simplify delegated events
    - kerijs
    - kerigo
    - kerijava
    - keridht

- Other topics?
    - IIW is in 2 weeks
        - demos?
            - interop might be tough to organize at this time
            - issuance/verification/revocation(?) of verifiable data chains possible
        - inclusion of a self-addressing identifier within the data container it was made with, as a means of a "bound" identifier for that container
            - calculated using a default constant value for the digest field
    - updates from the gleif stream via AC/DC work
        - verifiable data containers may have their own identifiers
            - identifiers assigned arbitrarily have no cryptographically verifiable basis
            - a self-addressing identifier bound to the containers contents
            - included in the serialized form
    - microledger progress

- Issue review
    - [keri main](https://github.com/decentralized-identity/keri/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc)
    - keripy
    - keriox
    - kerijs
    - kerigo
    - kerijava
    - keridht

## Agenda Sept 21

- Implementors update
    - keripy
    - keriox
        - merged async streaming PR
        - fix in progress for delegation after delegation seals are removed from interaction events
        - FFI bindings: wasm
            - sled doesnt run in a wasm environment (system time/WASI not sufficiently implemented yet)
            - Ivan: the DB/Store could be implemented in other ways for wasm, e.g. hash tables
            - Robert: in a browser env, lack of keys available to import securely can limit usage
                - Ivan: there are ways, key management entirely within wasm, or other means
            - Can pass browser implementations of relevant key management APIs to the wasm context, to use within wasm
                - Ivan: this doesnt fully secure the call-stack from potential mismanagement/manipulation
    - kerijs
    - kerigo
    - kerijava
    - keridht

- Other topics?
    - Update call between this group and the gleif group
        - pending clarity on potential IPR issue of sharing progress/work
        - information that falls under the categories defined in the WG charter being shared by parties that havent signed the IPR release with parties within the WG is an issue
    - microledger (robert)
        - data model providing a data provenance log with hashes linking the log events together (e.g. a KERI KEL, GIT, Ceramic Stream, Textile.io Thread, etc.)
        - applied crypto WG is working on a generalized version to share between "applications" implementing specific types of provenance logs

- Issue review
    - [keri main](https://github.com/decentralized-identity/keri/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc)
    - keripy
    - keriox
    - kerijs
    - kerigo
    - kerijava
    - keridht

## Agenda Sept 14

- Implementors update
    - keripy
    - keriox
        - reviewed PR #79
    - kerijs
        - KERL replay logic
        - event format fixes
    - kerigo
    - kerijava
    - keridht

- Other topics?
    - kickoff meeting of Decentralized ID management working group (robert)
        - under [CEN (european standards committee)](https://cencenelec.eu)
        - over 30 participants
        - EIDAS 2.0 from ETSI being proposed
        - focus on interface for sovereign wallets for interop
        - standard aimed at being agnostic (no assumption of DLT or blockchain)
        - most participants not in favour of implicit DLT basis
        - different systems provide different features/guarentees of data persistance/mutability/assurance which cannot be assumed by any spec
        - all participants desire stronger sovereignty for clients in terms of PKI/wallet infrastructure
        - [StandICT](https://standict.eu) (?) provides grants for open standardization efforts up to 10000 eur
    - topic(s) at IIW
        - potential discussion of various microledger techniques and systems (robert)
            - all towards "zero trust data management": systems with direct commitments to data
        - GLEIF will present their progress on KERI integration/usage
    - Joe Andreiu podcast
        - either Oct 27 or Nov 3, 20:30 CET
        - lets suggest Oct 27 for now
    - Update from Sam
        - keripy work has continued, focusing on issuing VCs
        - proposal for a call with the DIF group to provide specific updates
            - IPR concern with having external contributors discuss details of external work
            - lets ask balasz
        - goal of submitting a package of specs to the IETF towards the end of october

- Issue review
    - [keri main](https://github.com/decentralized-identity/keri/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc)
    - keripy
    - keriox
    - kerijs
    - kerigo
    - kerijava
    - keridht

## Agenda Sept 07

- Implementors update
    - keripy
    - keriox
        - merged pr about keys last week
        - review ongoing on async streamed event processing
        - could be broken up into smaller pr's
    - kerijs
    - kerigo
    - kerijava
    - keridht

- Other topics?
    - breaking out KERI sub-modules: Robert
        - feedback on the DID spec at w3c can be channeled into a plan for KERI spec organisation
        - KERI addresses many of the negative feedback points on the DID spec
            - interop deeper than the interface level
            - fundamental support for advanced features like multisig
            - not "ambiguous", lower integration burden, less workarounds
        - can the DID spec work be influenced in the direction of KERI design principles
        - potential adopters are anxious about DIDs because of security/interop/difficulty issues
        - can parts of KERI be broken out to be used in other ID systems?
            - complexity of KERI makes progress on implementation slower
            - decoupling modules make maintanence and usage easier
    - Joe Andreiu DID podcast episode on KERI
        - can emphasize the feedback on the DID spec and the desirable but uncommon features KERI provides that can be distinguished by the Rubric
        - Joachim will reach out
    - Applied Crypto WG: Steve
        - applied crypto wg seeks wider feedback and input
        - shared ideas about provenance logs/general crypto constructs
        - common foundations make all projects easier
        - existing project goal is just individual items of crypto material: signatures, keys, MACs, etc.
            - not complex objects like events, lists of keys, logs, etc.
        - robert: given a multisig key set, can a single key from the set be rotated instead of all of them?
            - steve: in KERI, the precommitment makes that model harder, as the whole set is rotated
            - robert: one could use multiple identifiers committing to a multisig transaction
            - imagine a tree-structured org, where a node in the tree must be changed to a new identifier

- Issue review
    - [keri main](https://github.com/decentralized-identity/keri/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc)
    - keripy
    - keriox
    - kerijs
    - kerigo
    - kerijava
    - keridht

## Agenda Aug 31

- Implementors update
    - keripy - no one present
    - keriox - 
        - 2 new PRs (commits got a little mixed up); 
        - big PR coming with CESAR streaming parsing; 
        - Edyta also raised on today for key handling (substantial review process) to break out priv from public keys in KERI key manager;
            -keriox manages state of keys, private key occluded from keri most of the time (outsourced to a TPM or HSM, for ex); we're working on a library that should be ready for review next week that separates out signing from KERI; KEL making it hard to break this out
        - moving away from neon binding to napi-rust, as former was problematic for npm
    - kerijs
        - no update; been away from desk
    - kerigo
        - no updates
    - kerijava
        - no steves present
    - keridht

- Other topics?
    - ongoing alignment with AppCry
        - [Crypto Data Encoding literature review](https://docs.google.com/document/d/10aHfefNVBrzFOiQ3--Ri7lMzwNqVOYsQqJal17uodvA/edit#heading=h.lddiqvpzsolw) (iterates on CESAR-like idea Dave presented here a few weeks ago)
        - AppCry's currently-accepted [work items list](https://github.com/decentralized-identity/crypto-wg/tree/main/work_items)
    - HCF - breaking out KERI building blocks:
        - KEL/TEL
        - Prefixes and sniffers
            - CESAR? 
        - Eventing?
    - Ivan: DIDComm and KERI: 
        - we've been experimenting wiht the idea of a DIDComm extension that can handle prefixes and CESAR parsing; KEL/TEL would be easier to parse if they were serialized in a more standard way (that could be marked down at runtime by different)
            - KEL/TEL interop is... hard to achieve unless the events making them up are serialized in a more common/standard way (JSON, CBOR, MsgPack, etc) and can be stored distinctly (even if they have to be translated to KERI encoding later to form KELs)
            - to fit into DIDComm events, even with an extension to add custom headers, they need to be serialized in more common ways to be the body/payload of a didcomm msg
        - Michal: Is yr DIDComm prototype enveloping KERI events before sending them?
        - Ivan: You're talking about the AnonCrypt way of JWS inside a JWE; direct messages don't work that way; (and yes, routing via mediators requires multiple additional envelopes and onion-style routing ensues)
        - Michal: I'm asking because I did a deep dive into CESAR last week; few texts to consult (recording from most recent IIW), where it seems **streaming** is assumed; how to reconcile streaming with envelopes?
        - Ivan: Yes, it's not a simple issue; streaming is not encrypted, though, and is exposed to various attack vectors (timing attacks, for ex.); revocation situations involving a blockchain-bound accumulator, for example, seems a bad fit for streaming... 
        - Ivan: Witnesses within a trust boundary, sure, stream away... but over public internet, I think we need to assume different security architectures
        - Chunningham: While KERI was optimized to *allow* streaming, I don't think there's any problem with enveloping and encrypting into distinct messages, everything still works; 
        - Ivan: For the case of KERI-over-DIDComm, I think there are optimizations possible (process based just on headers, for example, or parallelize on the basis of that); 

- Issue review
    - [keri main](https://github.com/decentralized-identity/keri/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc)
    - keripy
    - keriox
    - kerijs
    - kerigo
    - kerijava
    - keridht

## Agenda Aug 24

- Implementors update
    - keripy - no one present
    - keriox - Edyta - slow week, still refactoring error handling; Michal: trying to compile to WASM and... did not succeed, due to some dependency (SLED db) (Sled people already have an issue open... but nightlies show no progress on this); postponing WASM export and binding to JS with an FFI for now
    - kerijs - no one present
    - kerigo - no one present
    - kerijava - no one present
    - keridht - no one present

- Other topics?
    - CESR/related specs discussion at AppCry WG - [open google doc](https://docs.google.com/document/d/10aHfefNVBrzFOiQ3--Ri7lMzwNqVOYsQqJal17uodvA/edit#heading=h.lddiqvpzsolw) requests review

- Issue review
    - [keri main](https://github.com/decentralized-identity/keri/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc)
    - keripy
    - keriox
    - kerijs
    - kerigo
    - kerijava
    - keridht

## Agenda Aug 17

- Implementors update
    - keripy
    - keriox
        - Edyta: Error mode refactor underway now
    - kerijs
        - Shivam: Working on event replay capability
    - kerigo
    - kerijava
    - keridht

- Other topics?
    - SAI (Self-Addressing Identifier) crate announcement
        - Listing in rust [crates.io registry](https://crates.io/crates/said/)
        - hash-based/self-addressing only
        - dependency in KeriOx to make maintenance more efficiency?
            - prefix list is pretty stable anyways
        - extensibility by fork only? could a superset of prefixes be added on a fork?
            - ENUMs could use `non-exhaustive`, traits can allow extensibility
    - Node.JS contexts - could we be calling KeriJS instead of WASM-ized dependencies?
        - once keriJS reaches feature parity we can do interop tests
    - Using KERI for SSH
        - provide a module for [PAM](https://en.wikipedia.org/wiki/Pluggable_authentication_module) to allow anyone to use KERI keys to log in to a machine
        - leverage ACDC to verify authorization to different machines
            - revocable per-identifier authZs
        - Questions for the group?
            - Anyone have PAM module experience?
                - Shivam: I have some, from about 2 years ago; can reach out to ex-colleagues
            - Interest in weekend hack/prototype? Reach out to HCF (Robert in partic) if interested; Ox preferred (PAM crate? C-bindings?)


- Issue review
    - [keri main](https://github.com/decentralized-identity/keri/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc)
    - keripy
    - keriox
    - kerijs
    - kerigo
    - kerijava
    - keridht

## Agenda Aug 10 

- Implementors update
    - keripy
    - keriox
        - tables optimization PR #74 merged
        - SAI extraction (as a feature)
            - used for ACDC, other tools
            - generic identifiers of all kinds (keys and hashes)
    - kerijs
    - kerigo
    - kerijava
    - keridht

- Other topics?
    - Followup from Ivan and Robert re: AuthZ issues for KERL propagation policies?
    - News
        - Human Colossus Foundation continues on authentic data economy project
        - got accepted to work on KERI ID management tools as part of the ESSIF Lab infrastructure program
        - ESAN will meet on 18th for discussion on decentralized identity
            - working group 01 on Decentralized Identity Management

- Issue review

## Agenda August 3

- Implementors update
    - keripy
    - keriox
        - indirect mode stuff
            - runtime for witnesses
            - interactions between indirect mode participants
                - requesting ID state from witnesses
                - receipt generation for key events
                - db purging when witness is rotated out
        - building on existing PRs, waiting for review
            - db changes
            - async cesr stream processor
                - sniffing first bits of message
            - key store/management trait integration
    - kerijs
        - blake2b/2s/3 support
            - using [hash-wasm](https://www.npmjs.com/package/hash-wasm)
    - kerigo
    - kerijava - vacation backlog
    - keridht

- Other topics?
    - Spec status update
        - no change - still waiting on IETF-channel future steps
        - 
    - interactions between identifiers/parties in indirect mode
        - allowlisting of witness doesn't feel robust enough for all witness-identifier interactions; can any identifier witnesses by a given witness ask for the KERL of any other identifier witnessed by it? I am not sure this approach is flexible enough for all use-cases
            - some kind of handshake or permissioning model for witnesses to propagate KERLs? This is not in the whitepaper, kind of a variant, so I wanted to discuss with others
            - Charles: Is this an AuthZ issue? Ivan: More broad than that: should trusted and untrusted/unknown identifiers - some kind of logging distinction seems needed
            - Robert: "Governance Authority" is the way to abstract out that kind of propagation policies per jurisdiction/context; for example: GDPR mode, consortium-only mode, allowlist mode, trust-registry-only mode... whole spectrum from "share KERLs with everyone" to "only share with pre-registered identifiers"; HCF has been discussing fractal governance authority to enable very complex 
            - Ivan: I see the value in that abstraction/top-down approach, but I'm worried about the low-level implementation primitives that need to be in place to implement/support all those options above; I did it with seals, but I'm unsure that's an appropriate place to go off-whitepaper
                - Ivan: "Wildcarding" primitive?
                - Charles: But does that require an extra field? Does each seal carry with it information about which policies to apply? 
                - Robert: But what about malicious witnesses who ignore that policy anyways? Ivan: Separate issue 
                - Ivan: Not talking about solving the problem in the KERL, I'm just proposing an anchor
                - Charles: I think that policy lives in metadata/witness list, not in each KERL
                - Ivan: Would that policy/metadata query happen outside of events?
                - Robert: Separation of concerns: KERLs are deliberately minimal for performance as well as separation of concerns reasons; policy should happen outside since it has to be ENFORCED OOB anyways; going into indirect mode is consenting to propagation, policies enforced by network actors (not just witnesses)
                - Ivan: Interaction events used as some kind of policy basis/primitive?
                - Robert: But KERL has to have no policy info in it to keep from leaking that for configurations where it ISN'T needed; better to enforce network policy one layer up in network
                - Ivan: Of course, there is the base spec and witness can be more or less
                - Ivan: architectural qualm, tho: if witness controls all policies...
                - Charles: But identifier/controller policy TRUMPS witness policy...in particular, an independent [VC] TEL can be controlled by one identifier and only shareable with an allowlist it contains Ivan: But doesn't that constrain discovery?
                    - Robert: THat's why we're applying TOIP's ACDC AuthZ model for how identifier policies mesh with witness types/policies; for example, imagine a VC or a network where no KERLs can be shared with a requested from a network in an embargoed country; or, anti-spam example; witness infrastructure will need to be flexible and reactive to these kinds of policy variations; infrastructure is richer if it doesn't require any KERL contents  
    - Robert HCF: extracting from keriox the self-addressing identifier library?
        - OCA used DRI; ACDC also needs some kind of self-addressing identifier for references; breaking out a distinct library and/or spec for the self-addressing 
            - licensing, spec... separate crate (and/or JS library)
            - ACDC implemented through git hooks
        - Iván: Feature gates on keriox?
        - how diff from CIDs? <- same intent, different aesthetics
        - Dave: I've been doing it a different way, to avoid W3C-conformant VCs, so I will dig into it myself and see if it works for my usecase
        - Robert: Come to the [WG meetings](https://wiki.trustoverip.org/display/HOME/ACDC+%28Authentic+Chained+Data+Container%29+Task+Force)! we've been using githooks
        - Dave: How do you get around the non-checkin policy? Robert: We're using workarounds until git team considers making it possible :D

- Issue review

## Agenda July 27

- Implementors update
    - keripy
    - keriox
        - async event processing with receipt generation
        - out of order and insufficiently signed event processing not originally implemented, may affect event process work with db table changes
    - kerijs
        - update to latest db model with tests
    - kerigo
    - kerijava
    - keridht

- Other topics?
    - IETF Spec process status
        - ongoing communication with IETF from DIF
        - Dave: TrustFrame has joined applied crypto working group for provenance log work
            - target work is a superset of KERI features (generalised provenance and data authn tools)
            - working group is being developed as a launching pad for specs adjacent to this target
            - KERI/CESAR not adopted in favour of a more general/adoptable framework for signed data/roots of trust
            - common features of KERI and provenance logs can/should be developed in applied crypto wg
            - how to get involved?: join applied crypto wg, attend meetings
            - group work encompasses not just signature suites but higher-level data formats/protocols e.g. provenance logs
            - work items must be backed by >1 organisations
            - convergance in specs would allow KERI to fit into the applied crypto wg model of primitives and crypto infrastructure/providers/consumers (cryptographic services protocol)
            - KERI WG members could participate in software supply chain work (PKI for attributable software contribution and distribution, data provenance for software/binaries)
            - ideal goal is convergance of as much of the stack as possible for interop, tooling and cooperation benefits
    
    - [keriox CESR](https://github.com/jolocom/keriox/blob/async/src/processor/async_processing.rs)
    - keriox processing db tables: OoO duplicate event processing
        - optimise tables and processing to minimize state recalculation

- Issue review

## Agenda July 20

- Dave - CESAR doesn't work in strictly-typed languages; it was hard to implement in Rust
    - Sidechannel resistance hard to do; runtime type inspection is a no-no in some languages; private key encoding/decoding code is highly sensitive, needs to be considered at some point...
        - table-based 
        - sygil (sp?) - high-speed capture to race-condition base64 encoding (OpenSSL has had to push changes because of this vuln)
    - KERIOX and CESAR?
        - Ivan: Not yet merged into DIF's keriox (PR pileup) but it's in the [jolocom repo](https://github.com/jolocom/keriox/blob/async/src/processor/async_processing.rs
) for now
        - Ivan: runtime inspection is just to look at first three bits (pretty quick); reject input and drop connection if unexpected/unaccepted type
        - Ivan: And we don't send private keys with CESAR anyways, no?
- CESAR <> Sam's [CDE](https://hackmd.io/@dhuseby/BkG-4gp2u) encoding mechanism?
    - Dave: I'm not trying to change KERI; i'm just arguing for a separation of concerns; what i'm proposing resembles LISP in the composability (and ordering) of lists --> data structures that maps well to provenance and logging; type codes --> use-case-specific structures represented by type codes; 
    - Ivan: But signatures don't match to keytypes 1:1; signatures of same type and diff lengths used for diff purposes; I think the type code table has lots of reasons to be the way it is... and it's a bad time to change any of that stuff!
    - Dave: provenance encoding stuff is going to git community and to IETF soon anyways... input from KERI that keeps those things aligned will create an adoption vector (allows KERI implementations to consume a whole set of data)
        - Git community won't accept it in its current form; Git wants to implement something in C (where variable length is hard to pull off, as well); Git is leaning towards SSB approach (sigil)
    - Charles - I don't see why char codes and crypto material encoding couldn't be adopted by the KERI spec; I'd rather have list-based structured data encoding (no reason why type enforcement can't happen at runtime for KERI!)
        - Charles: Hard to change spec now, tho...
    - Dave: Roadmapping/Harmonizing over time
        - Dave: Sam mentioned wrapping CDE data in a KERI-typed envelope...
        - Ivan: KERI could extend CDE encoding and attach additional KERI types
        - Dave: capitalizing experiment/stable [distinction](https://hackmd.io/@dhuseby/BkG-4gp2u#Application-Specific-Extensions) could work
    - Dave: CDE would also work for SSB and encrypted-email (linux kernel patch pipeline - conversation with Konstantin Ryabitsev)
    - Dave: This is going to git team soon for review; open to feedback over time
    - Ivan: Maybe it would help us assess and understand if we saw some examples of KERI messages (that our running code sends and receives) and 
- Roadmap talk
    - Dave's goals:
        - ASAP: hold a one-day conference with OpenSSF, Git, Kernel (Konstantin), KERI/DIF, Applied Cryptography DIF, and concerned parties to agree upon definitions, principles, goals, and survey the current projects/solutions under work and hope for spontaneous collaboration. Maybe a track at IIW in October?
        - August 2022: IETF draft standards for formats and protocols of cryptographic provenance
            - cryptographic data encoding https://hackmd.io/@dhuseby/BkG-4gp2u
            - cryptographic protocol for externalizing cryptographic operations https://github.com/TrustFrame/git-cryptography-protocol/blob/main/Git%20Cryptography%20Protocol.md
            - cryptographic provenance log abstract data model -> file format
                - anchoring receipt format
            - provenance log identifier (adi URN) construction protocol/format
            - provenance log locator (URL) construction protocol/format
            - protocol for anchoring provenance log identifiers with demos for public blockchains, SQL databases, DNS entries, LDAP servers.
        - ASAP: Convergence towards standard implementations used in critical tools (e.g. Git, KERI, TrustFrame open source products, other products/projects from other companies: Spruce? Human Colossus?)
        - ASAP: Proposals for moving from OpenID et al towards provenance log based authentication/authorization. TrustFrame is releasing Oberon protocol.
            - IIW session-string? one-day powwow/"Birds-of-a-Feather session"? 
                - Charles: 4 or 5 parallel developments needlessly replicating and diverging over stuff they don't NEED to be different
                - Dave: Cryptographic primitives in common; protocols for talking to EXTERNAL crypto tools
                    - Sidenote: why is git rolling its own crypto? It should "externalize" the operations and do them as close to key as possible
                    - Ivan: "Crypto as close to the key as possible"
                    - Dave: Google is doing this with FIDO, doing all the crypto on hardware devices 
    - Dave's advice: split specs into KERI-specific scope versus broader scope
        - provenance in non-web-based tech; internet-scale 
        - Charles: Original design goal was IPv6-linked hook for provenancing
            - Dave: But keystate/session-layer that could be more broad than IPv6 and be an internet-wide session layer spanning transports time-agnostically
                - Ivan: DIDComm? Session-based...
                - Charles: DIDPeer or some KERI-based ID systems are pretty close to session-based, trusted-storage-free...
                - Dave: 
    - Spec roadmap?
        - Charles: CESAR isn't likely to change much, and could be written now... but swapping CESAR for CDE or making a CDE-based version of CESAR would be a major change to do propose without the whole group
        - Dave: I implemented CESAR already so I'm happy to contribute to retro-specifiying it
            - Signature tables should probably be codified at least tentatively
            - Compose-messaging stuff
            - fields found in common key events seem unlikely to change
            - Lower-number KIDs seem least likely to change
        - Charles: Other stuff that could be specified:

- Open question
    - Ivan: Witness-Watcher comms never really described (not KERI msgs but more basic alignments, i.e., "here is an update for this identifier" or "I want to register as a watcher for this identifier")
        - how does a identifier initiate a witness? Is sending it an event with the witness listed as a witness enough, or is there an additional message needed?
            - Charles: DHT design open question? I think this needs to go to the broader group, because you're write that nothing is written yet about how to do that
            - Ivan: No interop...
            - Charles: We can always queue up proposals like our best guess of how to do this kind of thing (leave it on a feature branch)
            - Ivan: I'm prototyping a DIDComm message-type for those messages now
        - Charles: Not sure if this should be an Aries RFC, but you're describing an Aries sub-protocol, within DIDComm
            - Juan: DIDComm.org registry for [aries-independent] subprotocols
            - Ivan: `authcrypt` parameter makes it possible for bootstrapping
        - Ivan: Regardless of broader DIDComm compatibility/parseability, I altho think that a KID or sub-spec for witness/watcher comms might also be worth having for KERI's own purposes
            - Charles: JWTs more generally might be worth considering
- Issue Review
    - [PR#74](https://github.com/decentralized-identity/keriox/pull/74)
        - out of order events processing - charles weighing in
        - Charles: gap in sequential event list remains visible wherever the OOO events go; if by "KEL" list you mean fully-validated events, that should be fine; what you need to worry about is sneaking in events via OOO mechanism; as long as VALIDATION STEP ensures OOO events get pruned if invalid (on a dead branch)
        - Ivan: They're not pruned, they stay there, but never get incorporated at identity incorporation event checkpoints
        - Charles: ex
            - inception, event 1, event 3 --> KEL of 0-1-3
                - Ivan: identifer state will remain at 1 even if 4 and 5 come in, validating 3... if 2 arrives later, identifier jumps to 3
                - Charles: what if 3 isn't validated?
                - Ivan: Can't rotation events be OOO events? Only second-party events should be accepted as OOO anyways.
                - Charles: returning to 0-1-3 example-- what if a second 3 comes in before 2? how do you know which one is false ?
                - Charles: performance gains on not re-processing queued events are major!

## Agenda July 13

## Agenda July 6 

- Intros & Announcements
    - Dave: Background and impetus for joining

- Implementors update
    - keripy - VC design continues, no updates
    - keriox - Ivan: PRs
        - 3 [PRs open](https://github.com/decentralized-identity/keriox/pulls) - 74 is top priority, plz look at it soon!
        - attachment annotation is still WIP; thanks to Phil for pointers on Slack to appropriate paragraph of KID
    - kerijs - Shivam regrets
    - kerigo - no Seth
    - kerijava - no Steve
    - keridht - 

- Dave's proposal to map out specifications of common tooling
    - CESR - pointers to relevant KIDs other than 001? possible subspec aligning TF work with KERI work?
        - other hackmds? Sam sent me one, not sure if there's other stuff I should be looking at 
        - context: OSSF project for gitsigning beyond OpenPGP & X.509
    - IIW [session notes](https://docs.google.com/spreadsheets/d/1ChIF0DeIFqvnM23XuCwwidRk_E7nRhDZg11RbIih_eI/edit#gid=0)
        - common encoding format and event notation; TF invented one but happier to take something to IETF that's already aligned with this group
    - IETF form on my to-do list for this week - would like to take spec there
        - Hackmd work?
        - Sam: there are Markdown converter tools with IETF profiles built in as a template- custom heading tags and stuff
        - Charles: Spruce might be able to donate some of our resources to this spec in partic
    - Dave: The sticking point/debate point might be how to define "KERI-specific" subset of general-purpose version of CESR-- let's start descriptively and address that later, though, it's a big problem
        - "experimental" flag for forked/non-standards-track (//x-dash headers (deprecated))
    - Robert: Is there anything in the KID format that doesn't work? Could this just be a KID?
        - Dave: As long as that doesn't limit/prevent/slow down IETF timeline!
    - Editorial/Logistics - Start in a KID or in a new document?
        - Charles: I don't think addendum to KID0001 works well- i'd start editing straight into a stand-alone spec document for this 
        - Charles - Validate idea- specify the encoding bit in IETF while KERI keeps evolving so that we can point to a draft spec as we go?
    - Dave: another input to the CESR spec might be [this straw man](https://hackmd.io/@dhuseby/BkG-4gp2u) I worked up
        - pushback from OSSF/Git team on CESR processing model
        - .git TELs in porcelain (sp?) at least, if not in git core proper
        - Robert: HCF has been working on this problem from another angle, so we're sympathetic to the idea of KERI-enabled git
            - Dave: OSSF/Git interest - IPR logs beyond CLAs
                - contribution by KEL-recognition only
                - KYC + KEL = ?
                - actual eSig would be a requirement (eIDAS?)
                - Google also interested (they want FIDO tokens for eSigs)
        - Git community has its own politics - any help socializing self-describing cryptographic constructs
            - externalizing hashing and signing/verifying; keep Git agnostic to all crypto decisions
            - POLITICAL SUPPORT APPRECIATED - join the git mailing list and sign the praises of KERI and AIDs if you want to help
            - SHA1 and SHA256 hardcoded upgrades are the strongest headwinds - we're 3 years into a project to put these curves into GIT's code
                - "algorithmic agility" not selling over there :_(
        - Robert: is this git stuff public?
            - Dave: It's public... but entirely email-based
- Other specs worth starting/breaking out soon?
            - Dave: I've been posting patches and code snippets to the linux kernal git mailing list and search for my dwh at linuxprogrammer  dddott or g, you'll see threads about this project; check here: Public-inbox.org/git
                - Robert: Index of threads [here](https://public-inbox.org/git/?q=dwh%40linuxprogrammer.org)
            - TW: there's a learning curve to these git listservs... it rewards the investment, tho
            - Robert: Git is pretty decentralized! We're starting from the *legal side* how we can enable IPR mechanisms that are truly decentralized. Would love to see that repo you mentioned.
        - Dave: There is a publication requirement of this grant, which I will be updating some of these draft specs
            - inspired by GPG Azuan (sp?) - but I'm CESRizing the PGP sigs
            - but i need to point to a published spec; I'd love to have a spec-shaped edit here in this repo to point to (also helps git-internal politics)
        - Henk: I'm confused about how your hackmd and CESR - how aligned are they?
            - Dave: More like a cleanroom re-implementation of how I understood CESR 
            - Dave: And the hackmd I shared earlier is a tantrum at CESR, even
            - type tags stable in text - I wrote a PGP sig tool and it makes the signature types human-readable from the logs; the length-calculation in the CESR is one of only differences; 48-branch decision/flowchart versus 2? it's a strawman for debate, *NOT a counterproposal*
                - Rust-style serialization (serde) versus CESR (runtime type inspection)
                - checking length a lot easier than type+length 
                - Ivan: I think we should chat offline about how KERIOX is using serde...
        - Sam: check your email, I sent you some edits for that hackmd
    - event log spec distinct from event log handling KID?
    - Robert: keep KIDs KERI-focused, specs already earmarked for standards track in separate files
- Dave: I'll get started and bring whatever i've got to the group next week
- Dave: I could give the a version of the OSSF presi here if this group would like to see it
    - Getting OSSF interested in cryptographic provenance (that's identity-enabled...)
    - DIF's role in zero trust and software supply chain

## Agenda June 29th

- Implementors update
    - keripy
        - indirect mode prototyping proceeding quickly
            - passing info between actors
            - started from whitepaper security assumptions but designing interfaces requires lots of experimentation
    - keriox
        - Ivan: change in event logging storage per identifier; working on async processing for witness comms at runtime; this will allow unblocking of messaging across interfaces even on same core
        - Robert: Keriox + ACDC prototyping (HCF side) - will release soon
    - kerijs
        - Shivam out for the week
    - kerigo
        - Working towards KERI still :D 
    - kerijava
        - No news
    - keridht
        - Michal: We need this soon... we should devote some resources to this! Roadmapping discussion possible? Is someone working? Should we discuss?
        - Phil: Fulltime employee of GLEIF: we are running an implementation locally (can't discuss due to IPR matters); adapting to more recent KERIPY code on the GLEIF side
        - Sam: Conrad Rosenbach contributed code but it's checked in and he's not doing more; we have to work out implementation stuff ourselves; he built it against KeriPy (as developed back then-- requires updating for recent changes to keripy)
        - Robert: We need discovery mechanism - missing features? 
        - Sam: Basically functional, missing a few features and needs to be updated; not production-class but working to PoC standards already on our local machine; way better than the grad student project we discussed last Fall

- Conversation with Seth (LF): "Motion"

- Vote to move WG
    - Consensus versus vote
        - Juan Caballero (Spruce)
        - Shivam/Carsten 

- Robert - contribution
    - Kevin - IPR boundaries are difficult to navigate and understand - substantive contributions are blocked
    - Robert - no clear path for individual contributors is a big problem motivating this move from our side
    - Joachim - Jolocom's code contributions have been discounted
        - Sam - I meant only in terms of voting (where participation in the calls)
        - Sam - I also judged purely by github (Joachim - please review)
    - 

- Issue review
    - [keri main](https://github.com/decentralized-identity/keri/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc)
    - keripy
    - keriox
    - kerijs
    - kerigo
    - kerijava
    - keridht

## Agenda June 22nd
- Implementors update
    - keripy
        - Continuing design work for peer2peer message exchange 
    - keriox
        - merged witness threshold!
    - kerijs
        - eventing parts tests
    - kerigo
        - Seth planning to come back :) 💪💪💪
    - kerijava
    - keridht

- DIF/ToIP update from Sam (15 minutes)
    - document outlining IPR differences [here](https://github.com/decentralized-identity/keri/files/6694983/ToIP.DIF.individual.contributor.differences.pdf)

- Discussion
    - Indy DID method and the KERI tunnel
        - Kevin will reach out to Stephen Curran and try getting guest appearance in one direction or the other with the Hyperledger Aries call
    - Phil: Update from recent convo with Stephen Curran
        - DID Resolution to generate a DID Doc from a KERI AID anchored to an Indy ledger 
            - original proposal: Indy as discovery mechanism, but not as full witness
            - new proposal: 
                - Indy `nym` record and `attrib` record tweaks in future upgrade of Indy ledger code
                - anchor event to `attrib`
                    * endpoint for where to get full TEL, which can confirm the event in the `attrib`
                    * only witness listed in DID Doc would be the Indy ledger; ledger consensus rather than consensus between witnesses
                - current Indy DID Docs only have keys and one endpoint; adding BLS keys and additional endpoints could happen in the TEL and be ; signing and encryption keys can be derived from a single key with some key types (e.g. Ed25519)
                - keyAgreementKeys (KAKs) can be provided by witnesses/TELs?
                - PR on did:sov for special `attrib` for KERI that would allow storing a TEL-endpoint; custom resolver that constructs these 
                    - For more info, see [#149](https://github.com/decentralized-identity/keri/issues/149) - Terminology update: "witness" only refers to KAACE witnesses; Ledger-Registrar Backers (formerly a subset of witnesses) can be included in inception events and thus DID Docs
                    - Sidenote: this came out of TrustFrame convo, since they doin't use witness pools, only ledger-backed witnesses
                    - Not Indy Specific - could work for any other method that can write current key state (or hash) and an endpoint for proof of control/interactive proofs/etc and namespace-specific/DIDmethod-specific tunneling info in a txn that can be converted to a valid DID Doc by that method
                        - Keystate/TEL used to determine authoritative keys, not method-specific KMS
                        - ledger as secondary root of trust (equiv to witness pool)
                        - Seth: 
                            - Sam: IPFS workaround that some methods use: store DID Docs (statically) on IPFS and use the ledger as dynamic indirection/lookup mechanism for finding them

## Agenda June 15th
- Implementors update
    - keripy
        - exchange message 
            - three message types to date: "exn" msg, //raq msg to query state, and update message (for either TELs or KELs) 
        - Composable Event Serialization Representations (in KID001comment?)
        - wrapping CESR messages in pres exch/Present-Proof (v2?) messages (CESR//JWT proofs and LDS proofs) to harmonize over time with the WACI-PEx process
    - keriox
        - weighted threshold PR in review
        - request for PR Review from Cunningham (forthcoming!)
    - kerijs
    - kerigo
    - kerijava
        - refactoring for indirect mode attachment format, which will include the new CESR material
    - keridht

- Move to ToIP - still haven't heard back from 2 contributing members, will discuss next week


## Agenda June 8
- Implementors update 
    - keripy
        - refactoring to support "habitats" (environment for a given identifier prefix in each KEL): logic of how each event is designated local or non-local (security)
        - VC supply chain: issuer, verifier, etc
        - GLEIF test case: issuing VC from TEL and verifying it; revocation soon
    - keriox
        - additional DB implementation - non-LMBD but similar
        - minor fixes and patches
    - kerijs
        - eventing 60~70% caught up; will update when finished
    - kerigo
        - 
    - kerijava
        - 
    - keridht
        - code checked in a few weeks ago but no updates from conrad
    - misc
    - project usage/prototyping updates

- Announcement work on IETF spec
    - https://github.com/WebOfTrust/keri 
    - starting now because takes a while to spin up a WG
        - "Big Dog" pecking order/traction game - the smaller the proposer, the higher the bar for submitting a draft spec and garnering buy-in so that an "area director" will champion it and approve the WG
    - 
    
- Resolution to move WG to ToIP
    - Motion passed unanimously KeriPy, KeriOx, KeriJS, KeriDHT, represented in meeting. Awaiting email confirmation/response from KeriGo and KeriJava.
    - 

- KERI for novices webinars - [update](https://hackmd.io/5hp8BbDJTqm3bsTtZeHTJw)

- Bitcoinconf Miami 2021 vs. KERI
    - https://www.lynalden.com/bitcoins-network-effect/ LN on top of bitcoin can never do what KERI does?!
    - (https://i.imgur.com/QH5EiIm.png) bitcoin stack
    - [Bluesky](https://www.theverge.com/2021/1/21/22242718/twitter-bluesky-decentralized-social-media-team-project-update), Twitter’s decentralized social networking effort, has announced its first major update since 2019. The Bluesky team released a review of the decentralized web ecosystem and said it’s hoping to find a team lead in the coming months. The review follows Twitter CEO Jack Dorsey discussing Bluesky earlier this month, when he called it a “standard for the public conversation layer of the internet.” - **Relationships** should be portable! (e.g. number portability / forwarding service) 

- [Apple digital drivers licenses](https://www.msn.com/en-us/news/technology/apple-unveils-digital-drivers-licenses-partners-with-tsa-for-faster-airport-screenings/ar-AAKPxiC) - Is Apple trying to spoil the SSI party and will they succeed?

Older notes moved to
2021-1.md { [github](https://github.com/decentralized-identity/keri/blob/master/agenda-2021-1.md) | [hackmd](https://hackmd.io/JChTa9IaRxOxP1El5FB7PA) }
and
2020.md { [github](https://github.com/decentralized-identity/keri/blob/master/agenda-2020.md) | [hackmd](https://hackmd.io/eBKWws_uRZyq3aOTEKfHlQ) }