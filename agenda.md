# DIF Identifiers and Discovery WG - KERI work item

[![hackmd-github-sync-badge](https://hackmd.io/eBKWws_uRZyq3aOTEKfHlQ/badge)](https://hackmd.io/eBKWws_uRZyq3aOTEKfHlQ)

## Weekly Meeting Page

This page is for agendas and minutes of the weekly KERI-related work-item meetings of the Identifiers and Discovery (ID) Working Group, who are collaborating on topics related to DIDs and other identifiers. Meeting agendas are listed in reverse chronological order. Meetings will be recorded. This is an IPR-protected meeting, so please refrain from making substantial contributions orally on calls or on github before joining both DIF and the WG. You can get more information from the chairs or at [membership@identity.foundation](mailto:membership@identity.foundation). DIF membership info can be found [here](https://link.medium.com/PCtPmbHJV7).

Meeting Time: Every Tuesday, 10 am ET / 8 am MT (see DIF [google calendar](https://bit.ly/dif-calendar))

#### Links: 
[ID WG Charter](https://bit.ly/DIF-WG-select1) | Slack [channel](https://difdn.slack.com/archives/C0146LH5XQD) |
 Github Repos:  core , rust, python, javascript, go, and java | Public [website](https://keri.one/) | Helpful bibliography [ Wasm1 | Wasm2 | MSFT CQRS ] | ZOOM [ROOM](https://us02web.zoom.us/j/87321306589?pwd=MSs5dlJYR0hOYjBCbWJOSmR3TDQwdz09) Meeting ID: 873 2130 6589 Password: 293152


## Agenda 8 & 9 Dec - Use-Case and API Design Workshop

Agenda - presentations on use-cases (15min max please) + Q&A
* IoT 
* Immunity Credential Chaining
* Supply Chain 
* Others: GitHub issues welcome! 
* DID Method name: Un, Uni, Keri?

Tues 8 7-9MT, 3-5CET 
* 7.00: Confirm agenda, introductions
* 7.30: IoT (Michael Shea & Sovrin IoT WG)
* 8.00: 
* 8.30: 

Wed 9 7-9MT, 3-5CET
* 7.00: 
* 7.30: 
* 8.00: IoT pt2?
* 8.30: 

## Agenda 1 Dec

Announcement: Chained VC task force (still being chartered/convened in ToIP)
- authorizations left out of KERI until now: may alter course or scope of KERI?
- precedents/loose threads
    - W3C VC-core GH issue: adding authorization to usecases for VCs
    - chaining RFC in Aries that was discussed but was never implemented
- WG autonomy discussion
    - pros: maintenance, visibility, editor/chair approval of spec, sub-items
    - cons: who has time for a charter?
- 

Use case/spec hour
* Chained VC Semantic spec (updates to KERI spec?)
* Robert - vaccination use case related to ^
* Proposal for 2-char field name (Sam)
* Steve: Spec question- how to propose commentary where there isn't already some in the whitepaper?
* Thomas: use-case-independent "core spec" versus implementation and application-specific guidance (VCs, IoT/device ID, etc)


<details>
<summary>Notes</summary>

* Charles: Opened PR to move Kid4
* Thomas: what's the "core spec" of KERI? What's primary scope and what's secondary scope?
    * Sam: Plenty of non-VC and non-DID use cases! We need to keep KERI agnostic on all things namespacey (to make sure we don't hardcode DID assumptions into the system)
    * Sam: ephemeral, direct/p2p mode, witness/public mode (and hybrids); static versus rotatable keys
    * IoT use case (no DIDs or VCs mentioned) & rotation (of controling device)
    * Ned: is any key use case a KERI use case? what about a key exchange use case?
        * Sam: a non-identifier key, i.e. an encryption key or a DH key exchange key, could be committed to KERI
        * Sidenote: libsodium transforms between signing and encryption keys; Charles: KERI supports the x-Curves for this very reason, no? 
        * Sam: KERLs containing diff kinds of key lets them all share root of trust/auditing basis
* Robert: nagging question as I present KERI to cybersec experts: KERI versus PGP and early WoT thinking?
    * Sam: Differences b/w
        1. in WoT/PGP, there's nothing like a KEL to provenance derivations; each new key exchange required a new genesis key. Establishing AID each time is a lot of key-x partying. publishing KELs --> way less partying, persistent WoT
        2. Generic SCID as opposed to "trivial" SCID of public key; public key not only source of SCID derivation; ID can be bound directly to Key Mgmt Infra with KERI, requiring attackers to compromise both to compromise an ID
        3. Delegation for multivalent KM infras: transcends the classic security/performance tradeoff (in contexts with lots of signing), allowing smoother recovery from a compromised key
            * Speaking of multi-surface attacks, even compromising a next key doesn't get you very far without also compromising the delegator and witnesses (hurrah for thresholds);
            * Delegation also allows TEE/HSM integration
* Robert: DHT resolution process: how to bootstrap comms starting from one ID?
    * How's KERI sidestep DHT's classic sybil vulnerability? 
        * Sam: an honest DHT node won't accept a registration that hasn't been verified (by a witness's ID); 
        * Sam: DDoS attack is only real problem, but no one will accept an invalid IP anyways; signatures everywhere helps all of these surfaces be locked down by witnesses keeping each other honest
    * Signing is way cheaper now than 20 yrs ago (ECC) - let's use it more, and harden more surfaces!
        * SSL, for ex, skimped on signing (and went with authenticated/trusted encryption which was an achilles heel over time); signing after encryption allows attackers to probe/break the weaker crypto of the encryption;
        * See also new Kid3 commentary [file](https://github.com/decentralized-identity/keri/blob/master/kids/kid0003Comment.md)

Use case/spec hour
* Chained VC Semantic spec (updates to KERI spec?)
* Robert - vaccination use case related to ^
* Steve: Spec question- how to propose commentary where there isn't already some in the whitepaper?
    * editorial PRs welcome? Sam: issues a better place to start. 
        * Hank van Cann's new [Q and A section](https://github.com/decentralized-identity/keri/blob/master/docs/Q-and-A.md) might also be a good place to open PRs directly
    
    
* Thomas: use-case-independent "core spec" versus implementation and application-specific guidance (VCs, IoT/device ID, etc)

GH minutae
* Proposal for 2-char field name forthcoming - fairly benign (Sam) 
    * github issue & PRs --> changing field names in kid3 (and elsewhere?)
* Charles: PR to pull kid4 out of kid3 also forthcoming (unlikely to complicate each other)
* Kid versioning?
    * Charles: I assumed version numbers were not going to be very meaningful until combining
    * Sam: but implementations 

Agenda for next week's API mini-conference?
* use-case slides? unconference-style?
    

</details>

Dev Hour
* [PR](https://github.com/decentralized-identity/keri/pull/72) on delegation mechanics in kid3


<details>
<summary>Notes</summary>

PR on kid3 delegation tweaks - [PR](https://github.com/decentralized-identity/keri/pull/72) on delegation mechanics in kid3
    * already implemented in keripy but wanted to discuss before pushing to core spec
    * reasons 1 & 2 - delegating control authority of multi-valent keys-- authorization should happen at higher layers (i.e., in VCs...)
    * no delegation - 
    * reason 3 - multi-delegation use case?
    * permissions element cut
    * del rotation and del inc same as regular rot and inc, exc with a SEAL field
    * Ned: is delegation semantic described? Sam: Yes, but not in any KIDs, just in whitepaper
    * Major change: Delegated keys can't be used to delegate keys! nested delegation still possible, but only with interaction events, not rot/inc events.
    * Ned: The classical problem of delegation is rescinding; Sam: in KERI, delegation is cooperative (witnesses participate); one-way delegation doesn't weaken security; recovering 
    * Juan: Versus ZCaps and GNAP? Sam: Under the hood, this is sharing KMS, not creating new keys (??); this is cooperative, delegator/delegee need to cooperate for recovery and both need to be verified (via seals)
    * Delegation is the last to-do for KERI-core, so in Python at least we're functionally complete (if this is approved by the group)
* new semantics
    * Data contains seals (array of maps with labels)
    * config contains traits like "establishment only" or forthcoming "do not delegate"
    * delegation requires both data (seals) and config (do not delegate)
Key walkthough (test-delegating.py) 
    * thorough explanation
    * no real opinions or pushback-- no one had implemented delegation yet!
    
</details>


## Agenda 24 Nov

Spec and Use Case meeting

<details>
<summary>Notes</summary>

* config field (currently just used for a few settings) dictionaries
    * security feature - toggle to ignore interaction events & only log rotations & inceptions (that only locks down pre-rotated SCIDs)
    * data fields - seals for rotation events, inception data for inception events
        * Seth - this confused me when I was implementing-- better naming would help
    * perm (permissions) - as yet undefined (only used for delegated IDs)
    * Rename all three "payload" since no event needs more than 1 of the 3?
        * inception event needs them 
        * delegating with a seal 
        * anchoring with a seal
        * Seth: config felt like a placeholder to me? call it "attachments" (would imply a content-type)? (but perms seems important and separate)
        * Charles: perms should include structural stuff like "cannot delegate" (might need to be specified, or even JSON-only)
        * Arbitrary data - huge? digest/pointer?
            * Seth: How specified or arbitrary open should it be? Config field is pretty specified, but attachment could be pretty big...
        * Steve: Sam's Contract use case - can you bind
        * Steve: I'm coming from static-typed languages...
    * Sam: This sounds like DID-Core debates-- how extensible to be? Compromise: well-defined fields are defined, all else can be ignored by everyone else...
        * Steve: But if we want KERI to be minimalist, secure infra...
        * Sam: internal semantics get standardized and hard-coded into the code to avoid a fork... 
* Charles: some partners have asked about binding attributes about each identity subject 
* Charles: arbitrary key pairs are allowed, though, in other places?
    * Sam: is this the catch-all field for extensible data.
    * Steve: limit it to a blob structured per use case?
* Sam: Add a top-level "name" field to allow customers to define their own namespace for the contents of this field?
    * Steve: vendor prefix for labels
    * Sam: but a vendor prefix requires a registry... and everyone worries about squatters...
    * Sam: This protects the top-level namespace for KERI messaging-- contains all neologisms and 
    * Charles: Custom content in KELs seems iffy... do we really want to let people put app-system data in here?
    * Sam: Sure, but the point of using "seals" is to link data where it is (witness service can also be a data service)
        * directmode - they come to you for the data anyways
        * public mode - data lives with the witnesses
        * Seth: but won't people sneak data in there if it validates?
        * Sam: Not a URL/URI field-- only seals would validate, i.e. digests of data
        * Sam: Instead, this would require a discovery mechanism for the IP of witnesses (passing query params helps extensibility)
* Sam: we could lock down the spec not to allow arbitrary data, nothing except URIs in the URI fields and digests/seals in the d/s fields
* Sam: are 4char field names even human-readable in the first place? why "pre" and not "pf"? why "cnfg" if it's not really a config anyways?
    * Seth: But we're supporting binary and CBOR anyways, so it will never be all that human-readable...
    * Sam: A days' work to update all the field names
    * Charles: breaking change tho...
    * Ned: Is there a data definition language (DDL) in the middle here? like CDDL ? A CDDL would help...
        * Steve: We're kind of JSON-centric and need to be able to roundtrip JSON (in most cases)
        * Ned: CDDL can output JSON or CBOR, tho
        * Sam: Well, if someone wants to take on the work and open a PR...
        * Sam: All data so far is strings, so we don't need much of the featureset of CDDL;
        * Ned: I don't know offhand the differences between JSON and CBOR, but I'm pretty sure you can define "indices" in the CDDL that deterministically 
        * Ned: CDDL can be fed into a validating parser - you could validate earlier (i.e. validate the schema before you even get to the data)
* Practically - should we go to 2char field names? would CDDL help decode the field names?
    * Thomas: the issue isn't so much the namespace as the semantic space of custom fields...
    * Sam: Yes, semantic space could be bounded this way to just the protect top-level reserve words (global namespace)
    * Ned: I'm confused about the extensibility and the collisions... in CDDL, each layer is its own namespace?
        * I've seen semantics done this way in CDDL; there are still collisions and scoping...
        * Semantics get you to OIDs, which still have to be protected from colliding with anyone else's -- there's no magic formula, but CDDL 
* **Decision-time**
    1. add an extensibility field? decide again later?
        * Ned: But CDDL has a similar mechanism for extensibility? Should we check first if they're aligned or if there are corner cases?
        * Sam: Not urgent for use-cases we've already discussed... Charles: But I can predict future use-cases will use this
        * Sam: Keep people from using the spec-defined "semi-arbitrary" field for their own extensions
            * Sam: List/map grows over time/versions of the spec; not really arbitrary, but mapped according to spec-defined list
        * Steve: but why map? Sam: Perms and other fields that cluster and proliferate...
        * Ned: Not sure I see the additional value of having a map, if you already need to refer to a chart in a spec for the CBOR use cases... Sam: But this community's got DID Docs as its guiding mental map... 
        * Sam: labels for all non-crypto material contents
    2. 2-character labels in JSON ?
    </details>
    
Dev Hour - agenda
* Sam's Private-Key Mgmt library (w/API) in [keripy](https://github.com/decentralized-identity/keripy/blob/master/src/keri/base/keeping.py) & Edyta's KMS controller in keriox
* Test vectors - issue opened!
* House-keeping & in-group comms - let's use GH issues for bigger conceptual issues! slack is not archival, but perfectly fine for "am i missing something" or "where in the spec is X defined?"
* Continuing the 2char discussion

<details>
<Summary>Notes</Summary>

* Seth: Test vectors when?
    * Charles:
    * By analogy to the Aries test suite of unit tests?
    * So far, I've pointed my daemon at Sam's test scripts 
    * Sam: We keep talking about doing it some time, but no deadline set :D We need to just **publish** the list of events as vectors that can be validated
    * Sam: We've been waiting to finalize the list of event types (and thus message types to validate against)
    * Sam: Volunteers to write out other vectors?
    * Seth: Why not publish the dummy data from the test scripts? That's what I did to make unit tests for myself... push to KERI repo?
        * Charles: Note: these events were made according to the old prerotation logic, but it isn't really tested either way
        * Charles: 
* Steve: Questions about in-group comms 
* KMS extensions/API standardization 
    * Seth: But I thought KERI didn't touch priv keys ever?
    * Sam: it's not in the spec and KERI doesn't touch them, but it might need to standardize assumptions on what DOES touch them and how does it pass signatures to KERI :D
    * Seth: Go code is currently passing a "function" [name?] to KERI which calls that function when it needs a signature
        * Sam: Similar: Py and Ox versions are calling this a manager or controller
    * Steve: Java ecosystem has a lot of this already hardened into APIs
    * Sam: a well-written API would hide these details and divergences between languages and algos and libraries... abstracting to 
* attached signatures - self-framing rather than framed (not even newline chars)
    * receipts also structured (couplets and truples) and concatenated
    * JSON code allows multiple contexts (framed and unframed); Steve: this makes these into the general-purpose identifier for anywhere base64 is accepted, or? Steve: table tells the length to expect/splice in advance per prefix; Sam: can be binary, not just base64
    * Steve: codes a little cryptic to me as I was building - should we add something to help the devs?
        * sidenote: there's one hash missing a code, for ex. (not in the table)
        * Sam: Multicodec went that way, but it snowballs...
        * Sam: For foreseeable future, no single crypto library will be wide enough for us
        * Steve - we're reinventing x509 to some degree... let's not use ASN1 too
        * Charles: fixed prefixes - but many post-quantum ciphers are variable length!
        * Huseby's CCLang (signature verification language; // pay-to-hash in BTC); complex signature verification logic could be added later that verify variable-length keys
        * Sam: collective signatures also variable-length; op codes would be needed to parse those;
        * In summary, we're starting compact and limited subset, with lots of added complexity roadmapped for future versions...
* Sam's tour of his KMS extension
    * test_eventing.py manager object with 3 external methods: incept
        * incept (lots of variables with defaults): counts and seeds passed; recoverable salted variety and unrecoverable unsalted variety; tier=crypto strength (argon2: best pw hashing algo acc to a contest)
        

</details>

## Agenda 17 Nov

* Attendees
    - Sam Smith
    - Juan Caballero
    - Robert Mitwicki
    - Charles Cunningham
    - Thomas Hardjono
    - Seth Back
    - Steve Todd
    - Regrets: Shivam
    

Agenda
* Use cases - notes being collected here for future use-cases section of spec, and for spec organization itself [here](https://github.com/decentralized-identity/keri/blob/master/usecase_notes.md)

## Agenda 10 Nov

* Attendees
    * Sam Smith
    * Juan Caballero
    * Shivam Sethi
    * Charles Cunningham
    * Robert Mitwicki
    * Edyta (HCF)
    * Seth Back (HearRo) - Go 
    * Steve Todd () - Java
    * Ned Smith (Intel, DICE)
    
* Schedule API KERI Conference
    * Topics
        *   Web Adoptability. Should KERI events be JSONable Web consumable or at some other layer above?
        *   Should field labels be more compact 2 char max
 * Change Next digest computation to increase security in the case of multi-sig among distributed entities
     * Instead of concatenating values and then Digest the serialization. Digest the raw binary of each element seperately then XOR the result and then attach code.
     * Ned: Architecture Framework approach : map stakeholders and interfaces, then flows, before designing APIs for each interface
     * Scheduling topic calls- for most, the hour before the dev meetings better than after
         * Gather use cases and/or business cases (Juan prefers use-cases for SDO-friendly spec docs!) in extra topic calls with whomever wants to discuss
     * Extended Workshop presenting possible/strawmen APIs = Dec 8&9
         * 3-5 CET/6-8 PT Tues AND WED
         * Goal: 2 or more proposed APIs to share with external stakeholders after Wed
     * Extra Meetings - use cases and/or spec-authoring issues (attendance optional for all devs!)
 * multisignature design question
     * set of digests of each public key rather than full public keys needed for commitment to rotate
         * digest functions CANNOT vary - here the spec needs to be super normative
         * XOR + [digest of] threshold - 
             * Charles: if it's an XOR not a digest, should we use a diff derivation code?
             * Sam: No, it's contextual; context informs what the code means; saves us exploding the array and keeps the tables smaller
        * currently, threshold digest + concat of all pub keys, BUT instead this new XOR system allows controllers to each contribute multiple signatures and performantly deduplicating
    * Sidebar: hash algo agility?
        * Ned: Verifier decides which is strong enough; Sam: Actually, event decides and everyone else 
        * Ned: Could event be broadcast in multiple hashes? Sam: Not exactly, each event can only have one, BUT identifiers, rotations, and other types could use different hashes
        * Ned: TPMs and constrained environments are likely to only use one! Verifier needs to be able to support many, but policies/subnets will likely have to work in parallel? Won't there be implementations where multiple hash algos need to run simultaneously?
        * Robert: Windows Hello anecdote: each TPM only worked with certain suites, was too hard to find common ground hardware wise. bridges/translations possible?
        * Ned: I don't see bridges working here, tho-- Sam: yes, the commitments' portability and value only work if they're never translated! "changing even one bit in the commitment would result in a different identifier", the root of trust's lifecycle is limited by inception-event algorithmic commitments
    * BREAKING CHANGE ALERT
        * new KID: multisig support without a new protocol, if it's avoidable; to avoid the multisig bolt-on syndrome (common in the wild), we need to put 

## Agenda 3 Nov

* Attendees
    * Sam Smith
    * Juan Caballero
    * Shivam Sethi
    * Charles Cunningham
    * Robert Mitwicki
    * Edyta (HCF)
    * Seth Back (HearRo) - Go 
    * Steve Todd () - Java

* Minutes
    * Introductions
        * Seth Back (HearRo) - Go implementation coming along? Almost ready for direct-mode 
        * Steve 
    * Updates:
        * Robert: Testing Env - Travis CI/CD might be unnecessary, if github actions works?
        * Charles: OX updates 
            * partial progress on last few event types
        * eventDB: discuss 2 alternatives? 
            * approach 1: closely follows KeriPy https://github.com/decentralized-identity/keriox/compare/feat/14/db_traits#diff-23b4c110a535fa6df354073bab85cf1645400d08a9a202311db1d2898dc406bb
            * approach 2: follows usage from Kever and Kevery https://github.com/decentralized-identity/keriox/compare/feat/14/db#diff-23b4c110a535fa6df354073bab85cf1645400d08a9a202311db1d2898dc406bb
        * Sam: Discuss approaches to asynch/flow-based programming/architecture (can be scheduled, nonurgent) - halfhour session or full hour deep dive
            * helpful for understanding KERI as whitepapered; useful in implementing in bigger systems
            * Charles: my understanding of kevery seems timely
            * Seth: me too, it would help me understanding what I'm reading in the existing implementations
        * "Leaked" Data Governance Act draft (ping Juan on DIF Slack for a copy) - aggregation limits and "altruistic" carte blanche... there are some devils in these details!
    * 

* Action items 
    * Add Go and Java repos  KeriGo JKeri
    * Confirms GitHub actions will work (and has permissions) to run test environment in each repository

**

-   Seth Back Hearo  Go Implementation
    
-   Java implementation Steve Todd
    
-   Add Go and Java repos  KeriGo JKeri
    
-   GitHub actions to run test environment in each repository
    

**

## Older notes on [google drive](https://docs.google.com/document/d/1UVgMKGOjU_5bbgZH2WazNxUMRI0ucwDISrixd8WFxYc/edit?ts=5f034380#)

(garbled/malformed copy follows in case of google fail:)

Agenda Oct 27

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



	

