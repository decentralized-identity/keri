# KERI Project Work Item

(DIF Identifiers and Discovery WG)

[![hackmd-github-sync-badge](https://hackmd.io/eBKWws_uRZyq3aOTEKfHlQ/badge)](https://hackmd.io/eBKWws_uRZyq3aOTEKfHlQ)

## Weekly Meeting Page

This page is for agendas and minutes of the weekly KERI-related work-item meetings of the Identifiers and Discovery (ID) Working Group, who are collaborating on topics related to DIDs and other identifiers. Meeting agendas are listed in reverse chronological order. Meetings will be recorded. This is an IPR-protected meeting, so please refrain from making substantial contributions orally on calls or on github before joining both DIF and the WG. You can get more information from the chairs or at [membership@identity.foundation](mailto:membership@identity.foundation). DIF membership info can be found [here](https://link.medium.com/PCtPmbHJV7).

Meeting Time: Every Tuesday, 10 am ET / 8 am MT (see DIF [google calendar](https://bit.ly/dif-calendar))

#### Links: 
[ID WG Charter](https://bit.ly/DIF-WG-select1) | Slack [channel](https://difdn.slack.com/archives/C0146LH5XQD) |
 Github Repos:  core , rust, python, javascript, go, and java | Public [website](https://keri.one/) | Meeting [Recordings](https://docs.google.com/spreadsheets/d/1wgccmMvIImx30qVE9GhRKWWv3vmL2ZyUauuKx3IfRmA/edit#gid=1393617996) | ZOOM [ROOM](https://us02web.zoom.us/j/87321306589?pwd=MSs5dlJYR0hOYjBCbWJOSmR3TDQwdz09) Meeting ID: 873 2130 6589 Password: 293152

## Future/Pending Topics

- direct-mode interop updates post breaking changes
- replay mode refactor & witness logic rev

## Agenda 23 Feb

Use Case hour
- Guest lawyer to help with GDPR appendix to spec?

Tech Talk hour
- Interop testing (*cough, cough*)

<summary>
<details>Minutes</details>

GDPR issues
```
Q and A prio 1 General
 If you're using delegated id you have to delete the whole KEL?
 "tombstoning": the network can ask all nodes to ignore/not-process a dead identifier, which might not fulfill the right to erasure (even if it is right to be forgotten)
     - until this question is settled, KELs seem more definitive/compliant erasure
     - erasure corner case: if a legit request for erasure of identifier controlled by requestor comes in, but without keeping a "blocklist" of forgotten identifiers, I can't guarantee I won't replicate that KEL again later
         - Sam: as long as "internal" blacklist doesn't infringe, and erasure is only outward, this would seem to be fine?
```      

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
