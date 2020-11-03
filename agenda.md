# DIF Identifiers and Discovery WG - KERI work item

[![hackmd-github-sync-badge](https://hackmd.io/eBKWws_uRZyq3aOTEKfHlQ/badge)](https://hackmd.io/eBKWws_uRZyq3aOTEKfHlQ)




## Weekly Meeting Page


This page is for agendas of biweekly KERI-related work-item meetings of the Identifiers and Discovery (ID) Working Group, who are collaborating on topics related to DIDs and other identifiers. Meeting agendas are listed in reverse chronological order. Meetings will be recorded. This is an IPR protected meeting. To contribute, sign the relevant papers. More information from the charis or at membership@identity.foundation.

Open Participation: [medium](https://link.medium.com/PCtPmbHJV7)

Web meeting Information (Computer or Phone)
Time: Every Tuesday, 10 am ET / 8 am MT

### useful links
* For DIF members: Sign the ID WG Charter to contribute: https://bit.ly/DIF-WG-select1
* DIF Calendar [entry](https://calendar.google.com/event?action=TEMPLATE&tmeid=M21lcDQ2bzF0cDdhdmNocmk0Zmk4NXZxOHRfMjAyMDA3MDdUMTYwMDAwWiBkZWNlbnRyYWxpemVkLmlkZW50aXR5QG0&tmsrc=decentralized.identity%40gmail.com&scp=ALL)
* DIF Slack [channel](https://difdn.slack.com/archives/C0146LH5XQD)
* Github Repos: [ keri | keriox | keripy | kerijs | sam’s papers ]
*  Public [website](https://keri.one/)
* Helpful bibliography [ Wasm1 | Wasm2 | MSFT CQRS ]
* ZOOM [ROOM](https://us02web.zoom.us/j/87321306589?pwd=MSs5dlJYR0hOYjBCbWJOSmR3TDQwdz09) Meeting ID: 873 2130 6589
Password: 293152

## Agenda 3 Nov

*

## Agenda Oct 27
Memorable quotes
Private keys should never “come into” KERI or be used or seen by it at all
Exception: private keys in derivation codes, for use by imagined external components - never used inside of KERI; “self-documenting” crypto material generally good practice, for the low price of a few more entries in the derivation code table
Some architectures will probably involve agents storing self-contained pub/priv pairs 
(Indy/Aries ecosystem - multisig requires multiple agents, for example - TEE and HSM integration )
Potential URSA additions for KERI support
Email David Huseby, no response yet
Next work
KERIPy - cleanup then Delegation  and add Key State message to KID3
KERIJS - LMDB, more events + finishing eventing
KERIOX - DB/LMDB + cleanup + eventing
Test infrastructure
PR 55 contains ICP test events
Rename /testing -> /test
Set up Travis CI (in each implementation) to pull from dif/keri/test and run some unit tests
Add more event examples and event types as they are implemented
Add receipts and key state representation to the test vectors
Use for static integration style tests
API design
Once event types/data structures are all done, we can workshop APIs for watchers, witnesses, controllers and validators
Reference design for Controller which shows how they should be used (private keys stay out of core lib, but a reference will demo how the structure should look), taking advantage of common key infrastructure APIs
Can structure Controller to consume a dynamically provided key provider API
https://github.com/tpm2-software/tpm2-tss 
https://www.lightbend.com/blog/reactive-manifesto-20
https://www.reactivemanifesto.org
https://jpaulm.github.io/fbp/   Flow Based Programming Website


Multisig logic
async/escrow design allows for one less protocol/real-time alignment between agents; “async wherever possible” design principle? Events ordered at time of ingesting rather than along the way/in collection of multisigs
Bibliography: Reactive manifesto (2.0) and flow-based tradition (buffers to decouple dependencies and maximize reactivity)
Sidenote: Dictionaries (Python, 80s) > Linked Lists (70s)
SBCL (modern lisp) has dictionaries 
Clojure
TomJ: McCarthywrote lisp in the 60s! First language I ever learned, working on a ASR33 with a parenthesis problem…
Tom Jones: pre-rolled keys (pre-rotation) spoke to me; key recovery has bothered me for some time in many projects…; how stable are the messages?
Sam: But they might change, haven’t implemented all event types yet
Tom: Do you mean “message”when you say “event” (Sam: Event + signature, without envelope = [self-framing] message)
Casual chat
Charles: ToIP have a WG we should be talking to?
Robert: not that I know about…
Robert: Identifier working group (passive/active); originally proposed as “identifiers” WG, Drummond renamed DKMS group; but KERI doesn’t “do” KM; 
IIW! - Oct20-22 (Tu-Th)

Intros
Dave Huseby - Security Maven still? - COME ON IN, THE WATER’S FINE!
Crate builder? 
Joachim (Jolocom) - contributes to admin/positioning/comms roadmap items
Charles (Jolocom) - Github contributions welcome (primary editor of /keriox repo)
Joel Hartshorn - USAid dev eng - identity first, then blockchain, then identity
Micheal Shea - stalking KERI for a while - happy to try to help with writing and business - 
Use cases! PARTIC IOT
There’s already an issue open!
Michal (HCF) - /keriox contributor and also working on TDA 
Robert (HCF)
Shivam (Spherity) - /kerijs primary contributor
Steve Todd (independent) - enthusiast! Jive co-founder, knows Sam from them
Been working on a Java implementation JKeriLOL
Ajay Jadhav (AyanWorks) - interested in ledgerless 
WASM? or Node.JS?
Charles: React Native and Node.JS aren’t the best API; we prefer/recommend WASM wrapper from our experience
Deno.land? Consumes rust library and TS directly 
Charles: Git issues for advice on ergonomics, aesthetics etc of Rust APIs welcome!
John Walker (ToIP DSWG & CCI) - Semantic Web first, identity second; PHI focus; I’m just here to understand the roadmap and see where I can contribute down the road
Mark Lizar (ToIP DSWG; Kantara; etc) - Notice and Consent as EVENT/signature log - 
Sam: Georgia Law review paper on consent chaining
Mark: ISO crossborder consent paperwork (but begs the question of crossborder metadata-trackable identity)
Sam: Forensic compliance/auditability versus interactive crypto; automatic/passive signatures require less laws and regs to change
Mark: International law transfer use cases; consent ←→ surveillance is a hard circle to square without portable/standardized consent receipt semantics; we are working on 
Sam: Verifiable credential proves authenticity, not veracity (doesn’t line up well to legal concepts)
Mark: Event key logs are what we need to fit to legal frameworks from CA era - don’t want to skip that step!
Unified data control vocabulary (another ToIP project)
Roadmap Report-out (on-cam)
Joachim: development and other functions in parallel (spec writing and implementation guidance as well as marketing/positioning)
Messaging / FAQs:
Robert: Align with other communities? How to be more open to other communities or prevent reduplicated efforts? Provide the library for AcaPy?
Implementations (Py & Ox first)
Last two event types
Delegating rotation and interaction events - different verification process, involved delegation seal
Delegated inception and rotation events- different verification process
Witness library
Witnessing logic for KAACE 
Validator (depends on ^)
Watcher logic/calls
Networking (HTTP & UDP still pending)
Ajay: gRPC between two KERI agents? More bidirectional streaming options?
Sam: WebSockets (TCP tunnel); that can be added later for adoption purposes, but not necessary for core spec;
Sam: I’m more interested in standardizing APIs first 
Steve: HTTP has lots of infrastructure
Recovery 
Discoverability mechanism - for finding and getting the log anytime you have the [current? Or also historical?] key
Simpler version: Out-of-band / IP discoverability
Kademlia DHT - publication (equivalent of did resolution mechanism?) digest of service endpoint 
Ledger-based discovery for DID world
Charles: as many as possible :D
Cname: KERL:: A : discoverability mechanism 
Witness API  → Service endpoints that can be queried multiple ways
Robert: How do you get the service endpoint from an ID if that’s all you have? <20 minutes follow>
Proposed Action Items (within the WG)
Charter of new WG
Scope should include independent discovery mechanism (will be separately donated)
But out of scope of core spec
Scope should include at least one popular ledger-based discovery mechanism (ideally today’s Indy)
But out of scope of core spec
Credential master issuance middleware/containers ; “Processing layer” (//Trinsic and Evernym’s DID issuance APIs); a KERI ID issuance API seems like the next step for scaling infrastructure and aaS models
 But out of scope of core spec
Reference wallet
1: Universal wallet spec + Keri libraries from Jolo wallet → https://github.com/jolocom/rust-multi-target
SemVer protocoling (major and minor have to align for trust)
Update Py demo (lessons learned from demo)
Console options
Verbose error methods (debugging mode)
Curves needed for 1st release
secP256k1 helps with NIST compliance
DAVID: SEND ME A DELTA OF THE CURVES YOU NEED IN URSA 
Workshops on architecture mapping in WG (for documentation parallel efforts)
Integrate KeriPy to AcaPy (or maybe KeriOX, with appropriate wrapper, for AriesJS) 
Issuing VCs against KERI IDs 
Michal: Indy is Rust-friendly
Mark Lizar: Use case pull request on international law transfer use cases or ISO informed consent receipt standards?
AriesJS - separate item, if AyanWorks or other AriesJS volunteers help-- Spherity not the best for this :D
Adoption within DID Community
Drummond & Indy Inter-op-athon: new namespace hierarchy for next V of did:indy (and Drummond is onboard to incorporate DID:Un/KERI)
DID:Indy:FINDY/etc:KERI - sub namespace 
“DID: <keriID>” might require some more substantial lifting in W3C
Deadline? As yet unknown; DID Core Spec reaches Recommendation when? (2yr charter ends Sept 2021)


















TODO LIST - MUST HAVES
Tunneling logistics: TCP easy ? is it worth doing Bare UDP or HTTP also? 
Jolo prototype has HTTP already!
EVENT Receipt Logging
[With exception of one NON-Direct mode feature: Witness event receipt ordering/fork check needed to avoid race condition on false fork (interaction event)]
[receipt logs not built out yet]
Replication of logs
IIW Sessions
Separate IIW Session: drafting DID:Un Method Specification? Will it be as minimal as DID:Peer
TODO LIST - GOODS TO HAVE/work items immediately post-IIW
Messaging between nodes: log request/flow, receipt request/flow, etc.
Fancier tunneling - secure UDP, performant HTTP etc
Spec language around TEEs and HSMs (see issue #54)
Delegated events (Enterprise / fancy KMS feature)
Witnessing (and receipt thresholds) elementals
Sessions IIW
Reminder: https://keri.one is live!
Noncon
Paul’s HCF/MyData session
SSI Meetup


Important: coordinate on Slack channel before proposing times!
Drummond: Keri “made easy” (!)
Sam: KERI Deep Dive
schedule AFTER Drummond’s and put “Part 2” in the name :D
Sam/Juan: Keri Roadmap - developer check-in/recruitment? 
Present draft of charter
Action item: do we have a draft?
Specification when? How? What kind?
Action item: DIF still has no definition of a v1 spec
Separate WG for KERI in DIF
Action item: draft of charter before day 1 of IIW! Juan available next week as needed
Timeline for spec text ← K.I.D.s
Sam/Charles: KERI DID Method  did:un did:keri 
Calendar in I&D WG before IIW! Charles will kick off the drafting with a description of how to convert KERI key state into a compliant DID:Doc
Share GITHUB link (not hackmd!) because its permanent
KERI Interoperability ?
Todo: coordinate with Stephen C and/or Drummond about interop sessions at KERI
KERI specification ?
Sam: Unified method for creating KERI-compliant identifiers
Zooko’s triangle - unpopular opinion that no single identifier can truly close the triangle-- KERI+ledger identifier is composite and meets all three reqs 
??: Business/use-case specification session OR DEMO on KERI?
Charles: Jolocom planning to do a demo of Jolocom-specific KERI use cases
DEMO TABLES
KERI direct-mode demo table
Jolocom demo table
BYU grad student Kademlia DHT discovery mechanism using existing Py code
Agenda - 13 October 2020 (Tu)
LMDB walk through and tire-kick
Py and Ox both using LMDB
Most performant for key material (used in LDAP as well)
Tour
Lines 180~220 - local failsafes/escrow in case DB connectivity lost
Environment = Main (fka master) DB; each table is a “keyspace”
LMDB API refers to multiple (historical) key values as “dupes”, updating value for a key as newest value in a pointered array every time you rotate/update a value (“b-tree”?)
LMDB concurrency mgmt: reads never blocked, writes “copy on write”;
Vocab: Put set get delete; get (all vals), put (add one new), etc; 
Vocab: IoVal (insertion order values): Get IoValsPreIter (for fetching and streaming all history to date before a rotation/event)
class Logger: combines/orders text - coordinates other sub functions
Escrow code not yet written
dgKey and snKey: “.” char not base64, thus encoding stuff; digest key or seq number key is prefix for all entries
Uniform formatting for all func calls: all are passed a “DB” (table) and a key; some also need a value to be written
“Content-addressable”-style DB - all keys indexed by their digested values (?)
Ordering- timestamping is easy to forge, and not definitive for ordering (hashchaining does this), but it’s still informative and useful for corroborating/reinforcing the primary ordering system…
.Sigs : identifier prefix ; value = concatenated signatures; escrow of partially-signed events hands them off to sigs once completely (allows asynch)
.rcts : 
Q&A
Charles: limited set of txns
Kever.py / logEvent() and escrowEvent()
Log event: 1. Create key, timestamp first, then write sigs, put in DB, and write seq number (“all of these are writing the digest”)
Seq number is like an index - 
Content-addressable-DB is a “dump site” for events; needs seq number to know where to look for it (fully-validated events go in KERLs, partially go in escrow tables, etc)


Quick alignment on interoperability for IIW demos
Databases storing receipts can be different; ordering of events into logs has to be perfect; only possible issues there are forks/bad events messing up the ordering
Sam: “A good demo would be two parties sending each other events, then showing/dumping logs afterwards to prove identical logs and state”


Agenda - 6 October 2020
Agenda clarification (and Q&A)
Shivam: Text encoding rather than buffering?
(needed for JS; PY does it internally?) 
Sam: LMDB uses a buffer, but on the KERI side everything’s copied anyways
Sam: Conversion and copying happens in same process (JS text encoder should be enough within that process)
Shivam: Oops, I built it using a buffer! Will refactor soon.
IIW Demo tables
Whitepaper updated
(Kid3) Receipt handling in resolving conflicts (sequence number in receipt message put back in to handle this cornercase)
KE verifier code: buffer underrun cornercase: missing bytes throwing exception rather than guessing/filling in; async 
Refactored PyMat SigMat : hidden methods are now byte-first for streaming optimization
TCP tunnel will get worked on this week (got sidetracked with above updates)
Feature freeze /code freeze on python code
Whomst will be ready for IIW demo table TWO WEEKS FROM TODAY?
Self-test (2 instances) of which implementation?
Charles: What’s the requirements, tho? 
Inceptions and Rotation events ONLY 
no signing or delegated events
no receipts
Python already reserved at demo table
Jolocom still on the fence on availability
How to prepare?
Sam: Code walkthrough?
Sam: Meeting late next week?
Remaining rust tasks for IIW
TCP listening loop
Receipt creation
DB implementation (not strictly necessary without delegation?)
Cross-test (1 instance each of two implementations)? 
Tour of code to go through “script” for demo in test_eventing.py
Dummy data defined up top for test vectors (should these be commented/annotated??)
Coe and val: two parties in direct mode
They send each other validator receipts, not witness receipts
Both are now logging their own receipts before sending in an “internal log” - this is good “hygiene” for event-sourcing anyways (helps everyone replay the same events by sharing/syncing local DBs)
Goes into the log “without any distinction between own events and others’ events”-- log entry looks identical in both logs (and both logs will be identical eventually)
This allows for both testing and assurance
Same exception raised from OWN events and from OTHERS’ events
Step by step through all the stages
1870~90: new code: inceptor writes receipt to own log, then creates receipt-message, then open TCP connection and sends it to counterparty
Bad receipt escrow (~1910ish) - probably best left out of demo
1970~~2020: rotation event and receipts written, sent, received, written
~2100: interaction events
Not checking receipts at the moment in the python code?
Interaction events in scope of demo?
Relatively chill, just increments counter/index and updates digest, doesn’t mess with key material
Stretch goals (if there’s time in the next week)
Key state message?
HTTP interface?
Q&A:
Charles: is full DB functionality necessary for demo?
Sam: Verifier logic relies on it? Might be faster to use it than to improvise verification logic without it!
Sam: Refresher of last week’s tour: 
Init doesn’t write to DB, but rotate does (multiple times in kever func)
Processing receipts hits the DB as well
Punted to next week: Tour/test of Sam’s TCP mechanism?
Discussion from last week about TCP mechanism:
Event Streaming first, web second
Choice between web socket (TCP-like stream;) and more restful combined post/stream (e.g. Firebase API)
Eventing.py analogy: coe would post inception event and proceed hierarchically (send:server::witness:client), or each opens a stream for the other with a websocket-like POST-stream?
Pros and cons: websockets harder to load-balance, but also harder to snoop on; Firebase-style restful approach more load-balanced (runs MongoDB under the hood)


Agenda - 29 September 2020
Direct Mode with validator receipts (transferable)
KID3 : added verbiage about transferible ID validators - pointer back to establishment event makes clear which keys to validate a given signature against (section “transferable Streaming EVent Receipt Msg w/Attached Sig”)
Transferable IDs seem more appropriate/common/necessary to direct mode, thus urgency
Tour through eventing with new, more complex test script between coe & val running new code
Update re: JS implementation
Spreadsheet mapping pieces
Eventing tour made sense to me; I can replicate/update my code accordingly after our 1on1 sync
HCF update re: Rust key material - working on rotation mechanics extension for now (not to direct mode testing yet)
Quick talk about test vectors, compliance tests, etc
Merge Charles’ pull?
https://github.com/decentralized-identity/keri/pull/55
Pending HCF review/meeting?
Roadmap checkin- anything that can be crossed off the list already?
Are there any GH issues to review? 
Tour of eventing.py to help HCF speed up their learning curve on rotation mechanics
Michal: Acapy question (Aries “protocols” for event streaming)
Michal: Assumptions of Aries agents: http-based, endpoints already known to each other; 
Sam: Yes, SSE  is restful event-streaming; 
Michal: loadbalancing question (sorry, I missed it); Sam: Aries optimizes for identity use cases, where non-restful, 2-way eventstreaming is less a priority; can’t bolt-on performance
Sam: Acapy-style protocol is fine, and we need one eventually, but I am interested in optimizing for streaming and for performance in v1
Contributing guidelines
Comment code plz!
Agenda - 22 September 2020
More roadmap talk:
Make KERI Working Group - worth the hassle for more visibility?
No objections
KERI core lib architecture: 
Recovery example
Updates to test_eventing.py (eventing.py updated around l530: stale event log tweaks to accommodate rollback in case of bad log fork)
Utility func in eventing.py to create receipts (had been missing); receipt msg not yet being parsed and logged, but that’s the last little bit missing from full direct-mode
KID0003 represents new receipt msg structure/data model (whitepaper out of date); further updated yesterday
Expose core features under a “object-oriented façade” needed for IIW demo ?
Combine facade with any communication protocol
Receipt Logs?
Direct Mode- don’t log receipts until signature check passes (requires escrow); if counterparty uses transferable (not fixed) identifiers to sign its receipts… can’t use the witness procedure/process
https://github.com/decentralized-identity/keri/issues/52 
Complex chronology-- escrow receipts while validating root identifier of the validator-counterparty itself
OpenAPI spec for HTTP based communication?
Jolocom’s P2P option versus HCF’s proposal for an HTTP mechanism?
Charles: inherited a simple tunnel from earlier work based on Resolution spec (??)
Robert: Trusted Digital Assistant architecture
DB agnosticism in core libraries/spec?
Sam: I made a façade in Py libraries so it would be relatively agnostic, but LMDB is a pretty good fit; 
Robert: HCF targeting multi-platform implementation: mobile agents, bluetooth, DIDComm-over-HTTP, etc-- the events should be able to travel between diff kinds of agents.
KERI API needed for this project? High-level ops and crypto primitives?
Sam: UI outside of agent model is a modular division of labor I support, in general; 
Sam: I’d like to see the dependencies called out in a more detailed version of this diagram in the future?

OpenAPI spec - we would like to work on this soon, so that we can work out the communication channel stuff
Sam: I hesitate to harden a spec (or an API) before building out a whole implementation, tho-- can we use a tentative API without committing to it?
Robert: But what are we using at IIW? 
Sam: I don’t have a communication channel mocked up yet, but I am confident I can do TCP/IP quickly and throw together a REST-based HTTP thing quickly (and fine-tune URL/URIs)
Sam: Simple Post/Get REST enough for IIW demo, no need to implement true stream just yet
Charles: This (PDA proposal) looks great-- do you have plans 
Rust crates? Libraries? How is this set up?
Robert: we are composing those components (natively built in rust); our vision is very similar to Aries but we are less focused on (optimized for?) VCs-- incorporate other data exchanges and flows
NGI - coordinating Covid VCs and other data exchanges
Charles: We’re also watching Univ Wallet and agent structure; let’s talk


task/project management for keriox
Github projects?
Finally sorted!
Agenda - 15 September 2020
Meetings now weekly!
IPR update with Rouven, Robert, Joachim and Carsten?
Specs written in github - in specup? In respec? In some other format, like Sphinx (fka Swagger), which just moved from RST to Markdown?
Rouven: core IPR problem: KIDs aren’t the “core IP” -- if whitepaper moves into DIF as a “donation” we can 
Sam: Moving whitepaper into repo is fine with me, waiving patents nbd on that
Roadmapping conversation
DIF WG versus WI distinction? 
Blog post and/or other public-facing comms? 
Joachim: Blog post should share Motivations, and Applications; should garner more interest and buy-in externally :D
Rouven: I would like a more agnostic messaging than “screw blockchains”, showing pro’s and con’s rather than silver-bulleting
Adrian: KERI’s privacy advantages over service-endpoint + blockchain methods?
Direct-mode Demo tomorrow for eSSIF-LAB (CLI with extra/verbose messages is fine)
IIW oct 20 - that’s in 4 weeks! Is essif-lab our dry run?
General administrative and technical roadmap
DID:Un first draft/outlined by IIW (!?!??!!)
TCP/IP port between any two implementations already 
Delegated inception events and DB stuff not ready yet on rust implementation
2 weeks from now, build the TCP tunnel and test it in WG
Charles - TCP could be integrated into CI/CD test 
Test vectors would need to be the same across all the implementation 
Docker setup needed
Tech talk
Charles: Self-addressing signatures in Blake2B Blake2S; both have output chunk size constraints (tricky to customize); tests were failing because prefix was expecting diff bitstring size
Sam: Blake3 is the same way, just less tricky to set output bitsize
Sam: The prefix should be updated (there should be diff prefixes for diff settings; since blake2 can output in either size, it should have entries in both tables so it can be looked up in either)
Shivam: Question about python test script for essif-lab mini-demo: Direct method node serializes and transfers to receiver, after validation, signed receipt sent back, right?
Sam: 
Issues in docu repo starting to pile up
#54 - 
#53 - Lifecycle events, transfer of ownership, etc ←→ Rotation
Non-transferable DIDs=locked to one set of keys ; only way to transfer is to “bootstrap” and throw away old identifier
KERI Witnesses use non-transferable IDrs; if compromised, start over, don’t rotate 
#52 - Key Rotation Rules (revocation versus rotation proper) - linked to DID-Core stuff

Agenda - 08 September 2020
Robert: Crypto Layer based on https://github.com/RustCrypto/traits ?
Charles: A good idea, currently the Ursa functionality used is only a very thin layer over these, and does not include Ed/X448 (or other potential targets e.g. P256)not 
Charles: Qualified material will still be useful/reusable (deriv codes, for ex.)
General consensus: Using a unified toolkit makes more sense that wrapping individual libraries
Test vectors for the Keri docs repository
Charles: look forward to my PR in next week or so?
Moving keriox into DIF repository, now that there is >1 implementer
Keri crate publishing (already published at keri v0.1.2, would like to add additional owners i.e. other keriox/DIF developers)
BerkeleyDB → LMDB (dB from LDAP)
Most performant of memory map DBs-- 
Alphanum sorting -- have to use keyspace accordingly if you want chronological sorting
Splitting keyspaces → segmented/distinct subsets of data→ “subDBs” or distinct “access models”)
Essentially just prefixes
“Copy on write”: helps with reliability 
Immutable specifics: not read/mod/write; concurrent readers don’t block each other, but read the older state; concurrent writers block each other (first come, first served); 
Exact log-append mechanics customizable: trusted writers can skip checks and append at end of queue, although that might be overkill here (and introduction corruption vectors on errors or inconsistencies?)
Tour of dbing.py
putVal and getVal = ‘overwrite’ attribute to handle collisions/blocks
putVal vs addVal : dupdata=true for both, but “dupdata” 
getValsIter - Py-specific efficiency gains 
dgKey (pre, dig) = digestKey generated from prefix and digest (for keyspace)
snKey = (pre, sn) - sequence number generated from seq number (no collisions possible due to hex vs __)
Counter Prefix in putIoVals - appended for LMDB sorting, removed later upon query
Duplicate entries work with “cursors” (to keep older entries), unlike Mongo and other document DBs; 
Definitions (in remarks at start of logger func): log 
New data model or table or etc for receipts?
Escrow (.ures) - escrowed couplets (unverified events waiting for signatures)
KELs .kels - keyed/sorted by pre + sn 
Separate escrow for out-of-order events or late-arrival (now meaningless) events
3rd escrow for duplicitous escrowed events
TODO items
Escrow cache/timeout/etc? (attack surface, after all)
Receipt storage rules/structure all tbd
Python-specific stuff: iterators and iter- variants of functions? Possible in JS and OX?
Iter in functionname
getIoValsAllPreIter - bring all duplicate/historical values since inception
Not passed a key - 
Sidebar: recovery after disputed events (aka credit card chargebacks for stolen private keys)
Slide 69 in KERI2 slide deck - “Revocery from Live Exploit of Current Signing Keys” 
Rewrite a disputed fork by using the pre-generated rotation key -- if both are stolen, S.O.L.;
Verifiable rotations replace/fork a duplicate non-rotation event, but non-rotation event discarded if duplicate to rotation event
Caveat: tons of rotation events → DDoS?
This rotation model has consequences for DB Design: how forks are handled
getIoValsLastAllPreIter -- gets all events needed to validate current state, ignoring forks; 
Dispute resolution = transaction-specific (KERI can’t do it, someone else has to) - disputed events stay in the DB; the other func, getIoVals will bring all forks and 
Directmode has no real mechanism here
Witness threshold at least has some mechanism that can cooperate with external dispute resolution
Compromised key → Race condition vis-a-vis witnesses; 
Interaction events are a trade-off, in design terms: logging them all creates more complexity and dispute-resilience
flexible/agnostic on signing infrastructure (delegation, multisig, etc); enterprise-grade KMS means you need recovery though, even if it’s rarely used
Dispute Resolution and recovery = hook for a feature, but not part of KERI 
Identity systems need thin layers to foreclose these rabbitholes
Key Event Verifier (and test code) updated in Keripy UPDATED to use LMDB - only chunk missing (commented out) but otherwise functional logging on both ends of a directmode KERI 
DID method name?
Action items
MEETING IS WEEKLY AT LEAST UNTIL IIW!
Agenda - 18 August 2020
Housekeeping- git hub permissions, IPR agreements, etc; 
Quick overview of recently-updated KID 3 (Serialization)
Tour of temporary internal testing apparatus for direct-mode development (sample DIDs hardcoded, a few events passed in as constants, etc)
Questions about key types, data model, wallet integration, roadmap
Agenda - 04 August 2020
Indy Interop-athon - how KERI can impact INDY implementation to help with “network of networks” 
Rust implementation questions:
URSA vs anything else e.g. sodiumoxide?
Implement a high level interface which is independent from the crypto suite.
Align derivation codes - seems that in rust we are using different then in python
Updated/Fixed
How to discover which identifier/event I am dealing with? Self-addressing? Basic? 
Context gives you the information, look up the derivation code table which gives you explicit information about type of SCI
How to find out which derivation can be used for what type of SCI?
See above
Are we providing the possibility to generate keys? How about SE? Where to store them? How secure them? What features we should have for key management?
For demo and dev purposes we provides API, maybe we should use Universal Wallet - wallet-rs 
Derivation code for secp256k1 public key T/NT?
Fixed? Reconcile/double-check together when Robert is here?
Align attached sig prefix code and 2-char sig prefix codes?
Sig config and attached derivation codes, what if they dont match but the sigs are valid and there are enough of them? Is it better to deprecate the sig config asap?
Addressed by the addition of a sig count code, to be inserted between the event and the signatures in the event stream/serialised form
Agenda - 21 July 2020
Get word out on meeting time  Move to 8 am MT every other Tuesday.
Sign DIF open participation  contributor agreement
https://docs.google.com/forms/d/e/1FAIpQLSc9jyJiSfu8kb6mLZK4nHfRHQQjb7XSzlmdfWfYlxJJg3qM8A/viewform
https://link.medium.com/PCtPmbHJV7


     
Updated Derivation Tables  Version 2.34 of WP
Robert: Changelog? Sam: Moving to github eventually (as plaintext .md file)
Updated KID-003
Rust development
Robert: Why WASM? Other wrappers might be necessary as well… we want as many as possible
Roadmapping
Robert: HCF Roadmap: Linux and Android for v1?
Charles: we got a minimal setup with Node.JS & React Native modules-- we could consider donating that code?
How deploy/github pipelines? How test against multiple?
Robert: Where’s the py build? Can we witness each other’s events or write to each other’s logs?
Aries multi-agent test harness (The BCGov one?)
Sam: Cryptographic attack vectors can be studied best with that kind of uniform testing (byte-lengths accepted, etc)
Robert: Harness = a candidate for a KID
Target for next IIW: “full event logs” in direct mode (minimum usable protocol for testing p2p or pairwise/ephemeral connections)
Direct mode: witness-free mode, both writing directly to their own KERLs and replicating them
Charles: Jolo is doing some stuff with DID Docs on top; 
Witness-replication/consensus deferred for later
Breakdown:Tasks for any [single] implementation in direct mode
1 Event generation 
Derived mode: private key → genesis event → prefix for logs
Self-addressing mode: genesis event → skeleton → hashes → public key and identifier → fill out event → sign it → log it
2 Event verification
Accept events by verifying public key and sigs on event, extract fields and compare to log
Check logs for duplicates/conflicts
3 Logging Apparatus
Deferred for Second Pass (indirect mode)
1 Delegation of events (needed for enterprise, complex KMS)
2 Witness infra
3 Watcher (Duplicity & inconsistency detection)
KIDs
0: Index of KIDS
1: core events
2: derivation codes
3: serialization of events
4: verification?


Agenda - 7 July 2020
Get word out on meeting time  Move to 8 am MT every other Tuesday.
Sign DIF open participation  contributor agreement
https://docs.google.com/forms/d/e/1FAIpQLSc9jyJiSfu8kb6mLZK4nHfRHQQjb7XSzlmdfWfYlxJJg3qM8A/viewform
https://link.medium.com/PCtPmbHJV7

Establish github protocol/flow (??min)
Merge review when?
Git Kanban Board as PM? Charles: +1
Big pulls? How big is too big? 1000s of lines in our fork…
60ish commits on the Jolocom/Keriox fork which would be good to PR
Robert/Charles to discuss, will bring agenda items to future call if needed
Signer config.: considering eliminating? Unnecessary redundancy or constraining step in verification?
Redundancy between indexes (included in each event) and ...
Use cases to be revisited? Are use cases involving multisig/backup signers worth including in v1 of the spec?
Biometrics keys, different levels of trust in different kinds of keys specific to context...
Problem with putting [unitary] key material into the event receipt, is that threshold/multisig doesn’t work/validate across multiple valid combinations
Standard mechanism now is derivation code attached to signatures, but something external may be necessary for more complex use cases
Attached signatures could be sent via signature header in HTTP… 
Design of optional checks/fields-- if nonempty then… versus if present then… (required and empty versus not present) - efficiency of event logs versus efficiency of code
Most urgent question isn’t v1 versus v2, but did we write it down somewhere and update testing suite/spec if we defer it to v2!
Collision risk between...
Attached-Signature derivation codes are unique to signatures, not derived from crypto material internal to the event
Initial-state spec as per Orie’s comment on aligning with DID:peer, DID:key and Sidetree and related debate in W3C DID-core (& ID WG)? (5min)
Passable via query params?
Keep an eye on, revisit later
Design decisions 
Queue mechanism? Append-only log/noDB functionality for KERL availability? 
On-Ledger Oracle as opposed to a witness-set - is anyone interested in that use-case? Is anyone thinking about a KERL-on-Ethereum instead of crawling whole ledger to look for events (KERL is thus portable and self-contained) 
Charles: we (Jolocom) were exploring this, but still immutable (GDPR) so we haven’t thought through it too far
Put in the Kanban as a project?
Longterm roadmapping/PM (5min)
Sam: If JS is waiting on the Rust, do the quickest, dirtiest temporary work to be replaced later by the WASM?
How to best parallelize (Charles-Shivam call this week)
Projects: EthOracle, DID:Un spec, Right-to-be-forgotten
DID:Un - Sam: I was gonna do it in time for IIW31; but maybe urgent for Jolocom? Willing to work sooner on that?
Meeting
Trying to attend: 
In attendance: Shivam, Charles, Sam, Juan, Rory?
Regrets: 
Agenda - week of 14 July 2020 **OPTIONAL**
(meeting for core/currently-active contributors)
RustCon2020: Charles and Robert Mitwicki 
Agenda:
Wasm versus JS bindings - decide across all for v1?
Pure JS → faster adoption, yet WASM might inspire more trust from a security angle; reusing the WASM might make less work for the JS guy?
Charles: *also* having JS might make for more completely autonomous (and comparable) implementations, but if we already have a full python impl… we already meet the “two complete implementations requirement”
Charles: if it’s up to me, I’d be happy with WASM
Sam: Division of labor: glue in JS that we can start on sooner?


Agenda - 21 July 2020
Library breakdown/topology (30-??min)
Logger (witness?)
Log-combiner/propagator (Watcher?)
Consensus Mechanism (Jury?)
DID Method --> Logger pipeline (Controller?)
Resolver (Validator?)
?? (Judge?)
Right to be forgotten mechanism
Queue mechanism? NoDB / append-only storage that might be retro-deletable?
Design decisions (15min)



	

