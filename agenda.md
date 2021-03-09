# KERI Project Work Item

(DIF Identifiers and Discovery WG)

[![hackmd-github-sync-badge](https://hackmd.io/eBKWws_uRZyq3aOTEKfHlQ/badge)](https://hackmd.io/eBKWws_uRZyq3aOTEKfHlQ)

## Weekly Meeting Page
``
This page is for agendas and minutes of the weekly KERI-related work-item meetings of the Identifiers and Discovery (ID) Working Group, who are collaborating on topics related to DIDs and other identifiers. Meeting agendas are listed in reverse chronological order. Meetings will be recorded. This is an IPR-protected meeting, so please refrain from making substantial contributions orally on calls or on github before joining both DIF and the WG. You can get more information from the chairs or at [membership@identity.foundation](mailto:membership@identity.foundation). DIF membership info can be found [here](https://link.medium.com/PCtPmbHJV7).

Meeting Time: Every Tuesday, 10 am ET / 8 am MT (see DIF [google calendar](https://bit.ly/dif-calendar))

#### Links: 
[ID WG Charter](https://bit.ly/DIF-WG-select1) | Slack [channel](https://difdn.slack.com/archives/C0146LH5XQD) |
 Github Repos:  core , rust, python, javascript, go, and java | Public [website](https://keri.one/) | A [note](https://tools.ietf.org/id/draft-knodel-terminology-02.html) on nomenclature used in this spec | Meeting [Recordings](https://docs.google.com/spreadsheets/d/1wgccmMvIImx30qVE9GhRKWWv3vmL2ZyUauuKx3IfRmA/edit#gid=1393617996) | ZOOM [ROOM](https://us02web.zoom.us/j/81492837711?pwd=OU01ZVpYYmdrcGJDNHhUWU5VNDkxdz09) Meeting ID: 873 2130 6589 Password: 293152

## Future/Pending Topics

- direct-mode interop updates post breaking changes
- replay mode refactor & witness logic
- interactive authentication mechanism for query protocol

## Agenda March 9


Zoom Link: https://us02web.zoom.us/j/81492837711?pwd=OU01ZVpYYmdrcGJDNHhUWU5VNDkxdz09

- [ ] [Check prepared answer in Q-and-A](https://github.com/henkvancann/keri/blob/master/docs/Q-and-A-Security.md#q-keri-is-inventing-its-own-key-representation-and-signature-format-why-did-you-do-that)

Specification:

Query Design Proposal


Development:



<details>
<summary>Minutes: </summary>

- 
</details>

## Agenda March 2
 
- Use Case Hour:
   * Please sign [new charter](https://bit.ly/DIF-WG-select1) before next github commit!
   * GDPR Review / Post-processing?
   * Query spec for querying replay modes
   * HTTP Restful interface
   * [APIGee API Design book 1](https://cloud.google.com/files/apigee/apigee-web-api-design-the-missing-link-ebook.pdf)
   * [APIGee API Design book 2](https://pages.apigee.com/rs/apigee/images/api-design-ebook-2012-03.pdf)
   * Restricted Modes

- Interoperability:
   * Docker containers

- Tech Talk:
   * Please sign [new charter](https://bit.ly/DIF-WG-select1) before next github commit!
   * Witnesses supporting witnesses.
      - Add remove and add witness lists to key state in order to support witnessing of removed witnesses on events
      - Two stage escrow for witnessed events
          
<details>
<Summary>Minutes:</Summary>

* Replay of GDPR discussion highlights:
    * block-list of "deleted" KELs for whom future events must be discarded - there are 2 exemptions to 'right to erasure'
        * a reciept of a request for erasure must naturally hold some PII, a two-party interaction might allow this to be recorded
        * a need to maintain system integrity/archival purposes can be a reason for maintaniing some info
    * right of erasure versus right to be forgotten - reflect two slightly different interpretations of the same article (which one people use is a hint of their school of thought)
    * regulations are only as effective as they are practical
        * if some witness maliciously keeps data and distributes it, they become subject to redress under regulations
        * GDPR is effective because liability is unlimited (disincentive for malicious parties is huge)
        * KERI makes it easier to stay compliant/not be accidentally malicious and reduces liability in that way (vs e.g. Tombstoning which is more of a grey area)
        * whats tombstoning? way to 'bury' transactions in a ledger (mark them as 'non-distributable' for stewards) such that they cannot be shared by legitimate stewards/nodes
    * most features of regulations are more about liability than technical restriction (placing liability upon operators for breaches of regulation vs restricting technique)
    * Charles: who is authorized to return KEL? Authorization needs to be addressed in Query spec
* Query spec for querying replay modes
    * Sam: Working back from watchers
    * Watcher's access/availability: 
        - identifier (and KEL?) of controller?
        - WHEN direct mode, privacy assumption: privacy between parties, no third parties need be (should be) involved... including ledgers
            - but other parties aren't technically STOPPED from publishing that info and breaking that privacy
            - security guarantees:
                - watcher has a self-contained KEL which is authoritative, but ONLY locally (because they're the only one who has it)
            - OTHERS CONDITIONS for delivering the privacy enabled at this layer
                - encrypted channel
                - consent/legal enforcement
                - some way of signaling/restricting behavior to honor consent policies, privacy compliance, etc?
                    - cf. restricted operation modes (~= trusted setup)
        - WHEN indirect mode, assumption: 
            - bad identifiers will be ignored and/or rotated away from (if transferible)
            - security guarantees: 
        * Direct/Indirect mode exist to imply these assumptions but can not enforce them
            - thankfully there's GDPR! :D
            - should the controller for a Direct Mode prefix's behaviour be limited by the spec re: distribution of KEL?
            - Spec could be opinionated, or could leave this to implementations (or make it a flaggable configuration)
                - Examples: DIDcomm handshake, Privacy-Compliance specs for banks
        - KERI: fewest features that support the broadest class of applications
            - concerns about maintaining privacy come from applications building on KERI, but as many features as possible should be supported
    * Query design questions
        - how to know what KELs to share?
        - one situation: "private witnesses" - trusted circle of witnesses that can query each other and "catch each other up" after periods of disconnection
            - Seth: So this is a form of indirect mode without publication to DHT/blockchain/etc
            - Sam: That would be one layer above-- permiscuous mode in the dB "defeats" (makes impossible) any mechanism one layer above that tries to restrict behaviors according to policies
            - Sam: AuthN at KERI layer, AuthZ one layer up
                - AuthN needs to be replay attack protection layer
                    - for instance, monotonic date-timestamp- request has a narrow time-window in it (acc to server clock, not requester clock)
                    - all requests monotonic to a specific signer - monotonicity requires recording last request received from a given identifier (sequential counter to prevent race conditions)
                    - MITM versus replay attacks
                - date-timestamp for NON-INTERACTIVE authN mechanisms (interactive authN tbd?)
                    - Server chooses to organize queries monotonically (no window, just counter) or as narrowly windowed
                        - windowed: slow or intercepted requests ignored (doesn't signal attack)
                            - simpler, less infra
                        - monotonic: sending multiple requests, all except newest come back with error message/explanation
                            - gotta store most recent requests, countered, in a cache
                        - Can't rely on HTTP so challenge/response has to be conveyed otherwise if we want interactive mechanism
                        - Henk: what about [TorGap](https://github.com/blockchainCommons/torgap/)? Sam: But I see onion routing as an enveloping mechanism, the core KERI message is the core of the onion
                        - Charles: It intuitively feels like a good idea? Sam: requests are signed, so this is specifically for replay attacks on signed requests
                        - Nick: Why not just encrypt the response or the channel? Sam: If you can assume an enc channel or layer one on, sure? The question is whether an option needs to exist for those use-cases that can assume that other-layer solution
                - Charles: repudiation or logging of responses? seems important to be able to prove that someone has given out info to the wrong parties? I'm voting for at least non-interactive authN for KEL replay queries
                    - Phil: making non-int a MUST now sounds good, defining interactive ; Nick: should do both, but wait on making the interactive a must
                    - let's open an issue!
                - Sam: NON-INTERACTIVE sketch:
                    - requester's identifier attached to request with attach codes, like a receipt, and can be used to check signature
                        - requests with bad sigs can be thrown out (they're unauthNd, after all)
                        - unlike receipts (which can forgive a little async), all requests have to be checked against latest key state of requester (standard key-based token policy)
                    - interactive to follow in github :D
            - AuthZ one layer above KERI
                - queuing mechanism ("que cue") kicks authN'd request up to controller logic one layer up
                - what else happens one layer up in the controller logic? all kinds of decisions and policies ("agent layer" in ToIP/Aries terms) -
            - "Survivable systems" design - failure impossible to protect against 100%-- detecting all failures (early) is far easier to achieve
         - bibliography for query design (from issue)
              * HTTP Restful interface 
               * [APIGee API Design book 1](https://cloud.google.com/files/apigee/apigee-web-api-design-the-missing-link-ebook.pdf)
                   - Sam: Good best-practices, practical guidelines for RESTful design for interested parties
               * [APIGee API Design book 2](https://pages.apigee.com/rs/apigee/images/api-design-ebook-2012-03.pdf)
   * Restricted Modes
        - Direct - witnesses sworn to secrecy (restricted mode)
            - first-seen rule for witnessed events is different: not "first-seen" until witness threshold met
        - Indirect - witnesses discoverable --> assume public identifier (watchers get those KELs, and get promiscuous with them) - Watchers' copy of KELs can be taken as authoritative --> witnesses run in restricted mode
      - Add **remove and** add witness lists to key state in order to support witnesseing of removed witnesses on events
      - Two stage escrow for **witnessed** events 
          - watchers holds events in escrow until threshold of witness receipts met - protects watchers from getting bad events, witness cache as a first line of defense against attackers publishing bad events
          - watchers first-seen rule requires all witness reciepts, witnesses first-seen rule requires just the controller-signed event
          - for events controlled by the controller that designated a witness, their designated witnesses want to accept events ONLY from controller
        - witnesses need to witness/create reciepts without seeing every receipt -> one-stage escrow
        - controllers could apply additional access controls on the witnesses they control
        - The witnesses
</details>

## Agenda 23 Feb

Use Case hour
- Invited GDPR specialist Alex Tweeddale (Spherity GmbH) will be here to discuss GDPR appendix/KID for the spec
- WG Charter - final edits requested (minor enough to do on the call) --> DocuSign this week?

Tech Talk hour
- Interop testing (*cough, cough*)
<summary>
<details>
Sam mentions the PR on the Py repo: My open PR is https://github.com/decentralized-identity/keripy/pull/82 - Kevin needs to check one thing with Juan then we can merge
</details>

### GDPR discussion Feb 23 2021
<summary>
<details>Minutes</details>

- Intros
    - Alex Tweeddale (self-introduction): master's thesis at Leiden, IDWorks (On Corda) Now active for [Spherity](https://spherity.com)
- CI testing update
    - working on branches now
    - Phil recommended disjoint replay for CI testing; comparing two runs to see if the correct KELs are reconstructed and deserialized
        - held back by not being done updating serialization on the SCOIR Go build
        - Go demo currently compares KEL results against target script (given in JSON)
        - replay mode to stream out to data file

- Problem statement re: forgotten KERI SCIDs and KELs
    - complete delete (no directive to never reconstitute) - allows replay/re-propagation later
    - blocklisted/delete identifier list 
        - charles: assurance of valid purpose
    - Alex: right to be forgotten request --> deleted data needs to stay deleted
        - Philip: 
        - Alex: Designated data controller = ?
        - Charles: Even harder to define control than a chain- each ID controller "controls" their own KEL events (nodes don't track all blocks or all "chains"-- hard to say what a node does and doesn't access to in terms of events)
            - each "identifier" (think, public key) is autonomous-- you only need to watch/store/process events about the identifiers you are paying attention to
            - Alex: //Corda - sidechannels/state maintained between parties, ignored by rest of the network (no global state, more of a patchwork of scopes)
    - Alex: Delete notifications propagate? how exactly does that work?
        - Charles: No discovery mechanism (or map of which nodes have info about a AID), so no 100% broadcasting mechanism
        - Alex: Individual nodes starting to sound like data controllers to me? Liability for notification/propagation of deletion request?
        - Nick: Keep all delete requests (both to prevent re-publishing them and also )
    - Philip: Query function mentioned last week: can you query someone to ask for a KEL of an identifier I don't control?
        - Charles: Not sure that's the intention of the query func; I can't think of how the AuthZ for disclosure?
        - Philip: Am I obligated to pass along deletion requests to all nodes I've passed KELs to?
        - Charles: Witnesses are the AuthZ - Watchers don't give out KELs
    - Juan: Are witnesses a broadcasting mechanism? Could they broadcast deletions as well as KELs?
        - Philip: Watchers are controlled by others, each controller has a witness; don't we have to tell THEM to delete as well?
        - Seth: Watchers are anonymous (for prot against eclipse attacks); queries to them are anonymous and they are anonymous, so you can't keep a list of which ones to propagate 
            - Witnesses push (to each other), watchers anonymously pull from nearest witness
- Alex: If there's PII, watchers would need controller's consent to pluck PII from witness
    - Philip: KERI allows users to use private identifiers in small groups- are users liable if KERI gives them best-practice options and guidance? 
    - [IPs are PII since 2016](https://www.whitecase.com/publications/alert/court-confirms-ip-addresses-are-personal-data-some-cases) aka "Breyer case"
- Sam: Right to erasure and right to be forgotten - diff?  Alex: Nope, same (but distinguished by schools of thought with different interpretations of the requirement!)
    - ALex: grey area, two schools:
        1. ICO UK - "putting data BEYOND USE" is the same as erasing it 
        2. true anonymization is impossible, so full deletion is needed (hashing isn't irreversible forever)
- Sam: Being a Party to a transaction caveats the erasure obligation?
    - transactions have shelf-lives (banks hold data 5-10yrs), but it has to expire eventually
    - all forms of legitimate interest have an expiry date; immutable stores are just not great
- Sam: What about non fungible assets?
    - signature receipts ?
    - Alex: that's... hard. i need to think about it
- Sam: KELs aren't commingled, each KEL is one identifier's hashchained history; erasing the KEL but keeping the identifier 
- Sam: Is persistent delete-list PII? Is hashed PII still PII?
    - Alex: Schools of thought vary-- if IPs are a "pseudonymous identifier", 
- Sam: The security guarantees of KERI are based on cryptography - more careful explanation of what's a hash and whether a deleted AID can be secured
    - keeping a hash of the KEL as a protection against duplicity
    - Alex: This sounds like the "archival" exception (which is part of the "balance" between individual rights and operational necessities, including security and protection against fraud)
    - Sam: Slippery slope: how to be certain the hash you've kept corresponds to deleted data
        - but the identifier (itself a hash, lol) is ON the receipt of erasure request
- Q and A prio 1 General
    - If you're using delegated id you have to delete the whole KEL?
    - "tombstoning": the network can ask all nodes to ignore/not-process a dead identifier, which might not fulfill the right to erasure (even if it is right to be forgotten)
    - until this question is settled, KELs seem more definitive/compliant erasure
    - erasure corner case: if a legit request for erasure of identifier controlled by requestor comes in, but without keeping a "blocklist" of forgotten identifiers, I can't guarantee I won't replicate that KEL again later
    - Sam: as long as "internal" blacklist doesn't infringe, and erasure is only outward, this would seem to be fine?

Fifty First Dates [problem](https://en.wikipedia.org/wiki/50_First_Dates requires that a receipt(signed copy)of a right to be erased request be not erased. The request includes the identifier that is to be erased. But the eraser is a second party to the erasure transaction request.

Charter Feedback from Steering Committee
    - Describe overall network topology including all roles within the KERI ecosystem
    - Describe how the various roles/services are incentivized
    - Describe/Analyze how the KERI network scales / e.g. with every maintained KERL / with additional actors
    - Add a sentence about the relationship with the I+D WG (where KERI started as a work item), by saying that the KERI WG may collaborate with the I+D WG on certain topics (e.g. adding KERI support to the Universal Resolver).


</summary>

## Agenda 16 Feb

#### Use Case hour
- ~~Guest lawyer to help with GDPR appendix to spec?~~
- Kid0001Comment  KID0001  updates  expanded count code table for replay support
- [Replay Roadmap](https://github.com/decentralized-identity/keri/issues/108)
    - WG consensus: build B1 and C first in reference implementation, then return to other items in B list
    - walkthrough of B2-B5
        - Seth: re: B3, allowlisting: How opinionated should the spec be on controller-witness relationship, i.e., replay mechanics? 
        - Sam: reference implementation for v1 should be general-purpose, but we can assume that over time, diversity of implementations and use cases will make complex variations on this
- Recommend reading: Keri versus CT [thread](https://github.com/decentralized-identity/keri/issues/94)
    - might be helpful for spec authoring? non-normative appendix
    - cf also [did:orb](https://trustbloc.github.io/did-method-orb/#self-certifying-decentralized-identifiers) - might be good to be able to map their propagation and witnessing terminology to KERI's for public-facing documentation

#### Tech Talk:
    
- Kid0001Comment Audit/compliance use-cases section
    - Composability
- Sam explains [Kid0001](https://github.com/decentralized-identity/keri/blob/master/kids/kid0001.md)
    - counter codes (=count codes) An index code is form of a count code, but counter codes are grouping codes, whereas index code refer to a given primitive, a count or an index.
    - we use the ordering in the list, which becomes important as soon as we're going to work on witnesses
    - There a cornercases explained in whitepaper (Section 11.5 Witness Rotations, starting with the paragraph that starts with,  "As an additional protection   ...")
    
> Sam: In the next version of the white paper I will create a subsection to better isolate that language. 

> As a note, This (joint confirmed witness rotation) may be an optional feature. It may benefit from adding a unique confirming witness prior threshold to establishment events. It could use as a default the prior threshold from the previous establishment event. However a any validator could choose their own prior confirming threshold. The only requirement is that old honest witnesses are required to also witness the event that removes them as a witness.
 - Post Quatum level X security + SHA3 discussed by Sam
 - Sam discusses JSON, CBOR, etc mappings in [Kid0001Comment](https://github.com/decentralized-identity/keri/blob/master/kids/kid0001Comment.md)
     - KERI supports all of the legal signatures [explained here](https://github.com/decentralized-identity/keri/blob/master/kids/kid0001Comment.md#legal-digital-signatures
 )
     - E-signing: Notaries are liable for digital signatures of their customers. So they want to make sure that customers have full control over the keys that they sign with. So that's why you have to pay for a notarized signature. For KERI this means that signature for the web are a totally different ball game than in the legal field. KERI makes the life easier of the notaries. "Have there been any compromises of keys for this signatory?
      - defensible audittrail -> "There is no duplicity today". That's where KERI comes in to play a role in the "traditional" adagia in cryptocurrency key management: I can't prove I am the only one controlling the keys to my funds and I can't prove that I've lost control over the funds". KERI says: If you think your keys have been compromised, rotate your keys. And this is exactly why people using ledger based systems like bitcoin or ethereum have a hard time managing their keys: you can't rotate them. The best thing you can do is move the funds around anc chard them.


- Test scripts
    - worth versioning Python so that test scripts could be commit-specific?
        - fractionally-weighted signatures and escrow not yet included in scripts


- Replay logic


<summary>
<details>Minutes</details>

- Replay Roadmap
    - signature accrual
    - translating between KERI native format and JWS 
        + Jolocom does this today?
        + harder to translate between distinct messaging and streaming; thus TCP as core engine for async engine
    - Async event verification engine (TCP-native) - more flexible on chunking, partic with escrow
    - Proposals for [roadmap](https://github.com/decentralized-identity/keri/issues/108):
        - A. redundant once B1 is implemented?
        - B1 + C = path of least resistance, unless people need B2-B4
        - Walkthrough of optional features to turn to after working on C
            - b2 - qb2 (30% more efficient over the wire versus qb64, which we're doing for now)
            - b2-2- cloned replay= all events + attachments in first-seen order versus sequence-number order 
                - Robert: do we need to replay every time? 
                - Sam: This is more like a bootstrap for propagating KERLs when you don't have confidence in the chain of custody and/or storage situation; if you trust your own storage since inception, no need!
            - b3 allowlisting 
                - no allowlist = "permiscuous mode" (aka development/debugging mode)
                - watchers keep it permiscuous (and accept all the )
                - Seth: how much is specified in the spec? Can't implementation vary in their allowlist policies or their roles?
                - Sam: The reference implementations should have this, but we shouldn't overspecify in the specs, as use cases vary on the volume and needs of watcher network, or witness security, etc; for example [#103](https://github.com/decentralized-identity/keri/issues/103) - controller-witness relationships vary, we're just implementing a general-purpose one (future witnessing models, incl witnessing-aaS, could evolve over time)
            - b4 - composable counter codes + text mode --> qb2, CBOR, etc
        - A: "Query replay" msg - way for two parties to request a replay from one another (and parameters)
        - C - needed for interop with existing systems, DIDComm, LibIndy, etc
            - c1 - Throw a KERI message in any encoding into an empty HTTPS body and set the mime-type and you're good
            - c2 - other headers
            - c3 - SSE stream (quick to implement if b1 already built) or web socket response?
            - response body that is a large JSON envelope (think DID Doc Resolution metadata - big top-level blocks for diff kinds of data: )
        - What should the spec specify?
            - query msg and syntax for replay
            - headers
            - SSE
            
After this we will do witness, watchers, jurors, etc
                
A query parameter (message, string) issue has been opened: discusses replay modes and options. -> [Query Mode Format](https://github.com/decentralized-identity/keri/issues/109)
    


</summary>

## Agenda 9 Feb

Spec and Use case hour
- Interop test review:  Take time to run CLI demos and observe results
- Continued from last week: Priority [One Questions](https://hackmd.io/Q92qKx1iTsGo49O7U-dDOg)

Techtalk hour
- nextkey changes because of weighted threshold
    - new serialization - python extendable to all languages? delimited list of ratio strings
        - concat for arrays, ","s for lists (no brackets)
- Update Witnesses (ROT event) question
- "First seen" with escrowed multi-sig out-of-order events
- Replay design:  
    - Database timed log
        - escrow timeouts different per seq numbers
    - KID0001 commentary
    - Extended counter codes as composition operators
        - required to iterate test scripts
    - new table- actual, actual append-only meta-event log - monotonic timestamp (might require microseconds) and/or counter variable
        - this could end up with watcher timestamps being useful for conflict resolution (but not necessarily definitive)
            - "compliant" timestamping mechanism (python 3 has mechanisms to make timestamps tamper-evident)
            - Steve - timestamping only needed within synchronized network (for gossip and load-balancing, for example)
            - Sam: every p2p network (including public POW chains) propagate within milliseconds or maybe a second; the only risk is if duplicity or collusion happens in that tiny window of time; 

<details>
<summary>Minutes</summary>

Spec and Usecase Hour
- introductions
- Charter logistics (2 chairs, ready to email to SC)
- interop updated
    - who wants to screenshare
        - Philipp: Go Bob, Go sam and Go-eve running against Python on our side
            - running diff on both outputs showing essentially identical output
        - Charles: We haven't tested it yet
        - Test scripts
        - concat for arrays, ","s for lists (no brackets)
```
1/2,1/3&1,1 // --example-- use language-specific fractional library to simplify!
→ "kt":[["1/2","1/3"],["1",,"1"]] 
```

- Update Witnesses (ROT event) question
    - changing witnesses weakens security that witnesses provide on control authority proof; 
    - escrow race condition solved by replay design - sequence numbers can be superceded by recovery event (self-healing forks, as it were)
        - interaction events can't supercede recovery events, regardless of seq numbers
        - table missing from database: order that events are accepted into log- the actual actual append-only event log, lol-- needs to be checked by this event-recovery mechanism
- Seth: would log compaction help?
    - Kafka and other event systems use this to guarantee some amount of performance guarantees
    - Sam; watchers would love a "light" event log, they are happy to just use a merklized version; they only need the keystate and the hash of the most recent definitive event for each identifier watched; all the other stuff gets handled separately, in other logs and tables like escrow and duplicity-suspected log; 
    - Sam: sparse merkle trees were invented FOR CT originally :D
    - only controllers and witnesses and probably validators need to keep everyone's complete log; watchers don't
- "First seen" with escrowed multi-sig out-of-order events
    - Henk can you clarify the "first seen, verified" doctrine?
        - Until something is written into a KEL, it's not verified; escrow unverified by definition;
        - asynchrony required for performance reason; this requires escrowing anything with 1+/N required sigs; 
- Replay design:  
    - Database timed log
    - KID0001 commentary
    - Extended counter codes as composition operators



</details>


## Agenda 2 Feb

- KERI Use Cases: Feature lack of block chain use cases.
- KERI made easy
- Question about weighted thresholds: Normative requirement to use fractional libraries so as not to use floating point numbers but true ratio math.
- Approve Charter for KERI WG
- IDNum - potential KERI Use case. https://idnum.global (20 min, Tim)
- Review Escrow status
- Directmode interop? Re-run the scripts from IIW
    - Py "canonical" (to avoid NxN compat burden and blockages)
        - against "major release versions" of Py - SemVer
        - dummy data testvectors from sample KELs ?
            - currently interactive only-- escrow could handle async
            - would it make sense to replay logs one line per second?
    - anyone added delegation to those scripts yet?
    - disordered events to test escrow?
    - multisig?
    - weighted thresholds - OX already integrated
    - tests will be defined in the python demo modules in the form of Eve, Bob, Sam, etc.

<details>
<summary>Minutes</summary>

Minutes
- Approve Charter for KERI WG
- IDNum - potential KERI Use case. https://idnum.global (20 min, Tim)
    - client = a telco with exclusive control of a mobile # range (only non-national number block)
    - we want to use global phone number range as basis of a personal digital identifier
        - https://en.wikipedia.org/wiki/Universal_Personal_Telecommunications
        - risks inherent in phone numbers as identifiers
    - Sam: Correlation? You said its blinded or masked?
        - Tim: uses RCS; an "overlay" for your existing SIM (gloperspecs?) to temporarily route your global number to your local number; sending a secure transaction from a wallet would route via local #; reduced/fixed cost for numbers 
    - numbers allocated decentrally (maybe not even with a blockchain?); owned by individual for life
- Review Escrow status
    - too early for code walkthrough? are other people implementing escrow yet?
    - escrowXXevent - 5 types, 3 functions each
        +OO - 
        +UR unverified receipt - 
        +3 functions: decide to escrow, process chit, save/discard
    - discuss with go and rust people?
        + Philip: do you have a loop processing each event against escrows?
            - answer: processEscrows() - not currently using co-routines, but should/will process all Escrows in parallel using yields
            - answer: they timeout
        + py implementation is written with lmdb-- the IoVal functions handle the particularities
            - sidenote: 100% of db entries have a date/timestamp field, even if KERI doesn't do much with it
            - witnesses/watchers use/trust each other's timestamps - BUT can check against locally-saved timestamp
                - see for example processOutOfOrders in eventing.py ("blogger" refers to Splunk-style verbose logs)
- Interop timeline?
- Directmode interop? Re-run the scripts from IIW
    - Py "canonical" (to avoid NxN compat burden and blockages)
        - against "major release versions" of Py - SemVer
        - dummy data testvectors created from sample KELs ?
            - currently interactive only-- escrow could handle async
            - would it make sense to replay logs one line per second?
    - anyone added delegation to those scripts yet?
    - disordered events to test escrow?
        - same set of events sent in a diff order by a new identifier = tests all cases
        - canonical set of tests
    - multisig?
    - weighted thresholds - OX already integrated
        - Charles: fractions versus integers? floats are bad! deserialize?
            - Sam: integers need to be normalized to satisfy thresholds; 
            - Sam: use a fractional library! Charles: OK fine... (also, >=1, not =1)
        - Steve: is WT standardized at all?
            - Sam: Only one random blockchain I saw used it
        - Juan: Where's this go in the spec? Explicit requirement or non-normative guidance?
    - tests will be defined in the python demo modules in the form of Eve, Bob, Sam, etc.

- Q and A
    - database variations and assumptions? notes for non-normative considerations? I worry necessary details of the duplicity detection might be assumed but not specified...
    - custom KMS? (SCOIR)

</details>


## Agenda 26Jan

- [wG Charter](https://docs.google.com/document/d/1AJWHjo3gicUcuQyYPjnncE1cf1_nz0Nzi5R1cDtbYbU/edit)
    - ONE WEEK REVIEW PERIOD - 
        - suggest-mode in google doc plz
        - please voice your objections (or those of your employers' legal counsel) in #wg-KERI, or in private
- quick editorial question: what happened to the delegation permissions field in [this para-KID](https://github.com/decentralized-identity/keri/blob/master/kids/kid0003_compact_labels.md)?
- Update from Sam on escrow processing (//buffer)
    - keeps any event w/insuffic signatures in escrow until `kt` met
    - delegated event escrowed until delegation event received and vice versa
    - Seth's question re: dupl events: two insuff-signed events (with different signatures, 1+ of which might have been false and gets dropped)
        - Sam: Py has a "likely duplicitous" escrow? 
- Steve - Directmode documentation is out of date?
    - swim lane?
- New Count codes for Replay Mode (may break/block Indirect mode but not direct mode)
- How to use KERI in a mode that obviates DID Docs.  Or Why all we need is KERI
    - Did resolver metadata and VCs. 
    - A did doc is an ersatz VC. We can obviate with a real VC.

## Agenda 19Jan

Agenda
- Charles' [issue](https://github.com/decentralized-identity/keriox/issues/57) re: updating prefix derivation post malleability-vuln fix
- Editorial updates from Juan and Henk
    - Juan: 'dig' ambiguity in kid0003 (only takes a sec, let's do it together on-call)
        - major facepalm as Juan realizes his editorial work was needlessly redoing work in a separate file in the same directory...
    - nix all TOCs?

<detail>
<summary>Minutes</summary>

- Introduction
    - Nick Telfer (indiv contributor, ex-Consensys, helping with Py implementation)

- Receipts as abbreviated messages or message-fragments
    - whitepaper terminology should be revised

</detail>



## Agenda 12Jan

- Spec & Use-Case Hour
    - DIF f2f [presentations](https://docs.google.com/spreadsheets/d/1hVnwrnU7QOp_rA7AcK2NTQkflSAg0zvQ3-We2DqyRpk/edit?ts=5fea38e1#gid=445783158) - 15min progress report out + side session(s) on interop
        - Enhanced recovery rules for cooperatively delegated identifiers. See additional language in WP 2.58 Sections 7.25 Cooperative delegation and Section 11.6 Recovery
        - Rust panel
    - Thumbs up on editorial pass to fix 
        1. [2char](https://github.com/decentralized-identity/kerigo/pull/4) issue in the strawmen?
            2. Juan will do
        3. [charles' diagrams](https://github.com/decentralized-identity/keri/pull/85)
            4. Juan will do
        5. fix TOCs on kid003
            6. Juan will do
    - Sam: Delegation-enhanced recovery modes (WP 11.6; new WP (2.5.8) has 7.2.5, 11.6 cover this)
    - Henk Q&A
- TechTalk hour
    - Details of fractionally weighted threshold support update Python implementation
        - Issues:
            - Extracted data algorithm uniqueness
            - Next commitment for fractionally weighted threshold
    - Enhanced recovery rules for cooperatively delegated identifiers. See additional language in WP 2.58 Sections 7.25 Cooperative delegation and Section 11.6 Recovery
        - Revised recovery logic.  
    - Custodial delegation


<details>
<summary>Minutes</summary>

- Introductions
    - new folks: Mikaela T and Philip F from (CANIS project)

- use case/spec hour notes

    - Sam: Delegation-enhanced recovery modes (WP 11.6; new WP (2.5.8) has 7.2.5, 11.6 cover this)
        - would be urgent to discuss if any implementers were already on recovery; no one (at least no one on the call) is there yet, tho.
        - review of cooperative delegation
    - Henk Q&A
1. [Not your keys...](https://github.com/henkvancann/keri/blob/master/docs/Q-and-A.md#not-your-keys-not-your-identity)
2. [relation KERI and VC model](https://github.com/henkvancann/keri/blob/master/docs/Q-and-A.md#does-a-keri-wallet-store-virtual-credentials-connect-to-my-identifiers)
    - Some source material in this [presentation](https://github.com/SmithSamuelM/Papers/blob/master/presentations/GLEIF_with_KERI.web.pdf)
4. [DEL](https://github.com/henkvancann/keri/blob/master/docs/Q-and-A.md#duplicitous-event-log) 
    - is it normative?
    - Sam: Validators need to track DELs (and blame their authors) for incentive model
    - Henk: Could they be reconstructed later if deleted?
    - Sam: Someone needs to!
    - Sam: storing and publishing DELs is a community service 
5. [Cooperative Delegation](https://github.com/henkvancann/keri/blob/master/docs/Q-and-A.md#delegations-in-many-systems-are-unilateral-keri-has-cooperative-delegation-what-is-that-and-why-is-it-better)
6. Anything in Q&A that currently has the reference "_(@henkvancann)_" could use an expert review. Anyone editing the Q&A: please keep in mind it's targeted at newbies in the KERI field.

- tech talk
    - Extracted data algorithm uniqueness
        * something something breaking change to serialization
            * paging dr chunningham, your signoff is needed in surgery
    - Next commitment for fractionally weighted threshold
        * tour of some validateSigs & kevers breaking changes re: signing thresholds
    - Q & A
        * Henk: why must prefix be unique? Sam: hash comes from inception event; any semantically-significant change to inception event would create a diff hash and thus a diff identifier (the self-addressing part); only the inception event are susceptible to txn malleability attacks

- scheduling an interop demo by the end of jan? 2Feb in 3 weeks? Try doing it in-WG meeting two weeks from now?
           
    
</details>

## Agenda 5Jan

- Spec time
    - hackmd badges on each KID
    - whitepaper changes over vacation - seal events, new math diagram  

- dev time
    - Ox updates
    - Issue review on /keri/
    - Layering/scoping discussion - things above the spec but may make sense for future specs and work items:
        - ACDC TF at [ToIP Technical Stack WG](https://wiki.trustoverip.org/display/HOME/ACDC+%28Authentic+Chained+Data+Container%29+Task+Force) - TF chartered and meetings already live
        - VC Issuance against KERI SCIDs? Might need a later spec
        - Wallet Assumptions? Does that require a spec?
            - Charles - Universal Wallet spec could easily be extended to make a new API - I could write something up eventually

<details>
<summary>Detailed Minutes</summary>
    - 
</details>
