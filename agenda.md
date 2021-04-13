# KERI Project - First Work Item - Core Spec

[![hackmd-github-sync-badge](https://hackmd.io/eBKWws_uRZyq3aOTEKfHlQ/badge)](https://hackmd.io/eBKWws_uRZyq3aOTEKfHlQ)

## Weekly Meeting Page

This page is for agendas and minutes of the weekly KERI-related work-item meetings of the Identifiers and Discovery (ID) Working Group, who are collaborating on topics related to DIDs and other identifiers. Meeting agendas are listed in reverse chronological order. Meetings will be recorded. This is an IPR-protected meeting, so please refrain from making substantial contributions orally on calls or on github before joining both DIF and the WG. You can get more information from the chairs or at [membership@identity.foundation](mailto:membership@identity.foundation). DIF membership info can be found [here](https://link.medium.com/PCtPmbHJV7).

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
- [use cases document](https://github.com/decentralized-identity/keri/issues/53)

## Agenda April 13

Review update IIW proposed Sessions
   - keri-dht-py

Updated KID003 with revised KeyState to include wr and wa lists.
keripy demos now support parsing hetero attachments with new count codes. 

First Draft of did:keri method specification
https://identity.foundation/keri/did_methods/

GitHub issue review

#### Minutes April 13

<details>
<summary>Minutes</summary>

- Round of introductions
- Review of the IIW session proposals on April 20th
- Sam: Anyone who has indirect mode running is invited to present.
- Robert: will create an issue based on the answers in Slack concerning TEL and namespaces. Sam suggest creating a slidedeck set of sheets.
- IIW Session are an hour long, we have three days and 8 session per day in our KERI track.
- We should be smart enough to choose a room and a timeslot not competing with popular topics.
- Juan suggest that KERI community members attend sessions that are close to KERI DID:PEER DID:ORB and join the discussion.
- DID:PEER is an intermediate step until KERI direct mode is live (in production). Sam is in direct contact with Daniel Hardman about the roadmap.
- Authentic Chained Data Containers: chain together attestions so you can provenance attestions. https://wiki.trustoverip.org/display/HOME/ACDC+%28Authentic+Chained+Data+Container%29+Task+Force
- Philip: DID:KERI https://identity.foundation/keri/did_methods/
     - Sam suggests to reference KID001. 
     - The normative specs in the KIDS should be referenced in the did method specification.
     - DID:KERI has the capabilities
- Robert: EU standardization commission on DLT/blockchain has installed a separate WG on Identity Management based on blockchain. Robert will keep an eye on this and keep us posted.
     - Sam: suggests to drop this new WG here and there during IIW
     - https://www.cencenelec.eu/news/brief_news/Pages/TN-2018-085.aspx
     - https://standards.cen.eu/dyn/www/f?p=204:7:0::::FSP_ORG_ID:2702172&cs=1465AF26367A9ECE85D149F31EF39162E
     - Robert: The group is called CEN/CLC/JTC 19

</details>

## Agenda April 6

- GH Issue Review
- IIW demoes? What people want to demo separately or together? 
    - indirect mode demo? turn on a witness pool and show witnessed events being logged (as first-seen, once threshold-witnessed) in non-promisc mode
        - Py and... Rust? 
        - Show Receipts
- [IIW](https://internetidentityworkshop.com/) Sessions to hold?
    - Whole WG - Indirect/
    - KERI Security - Guarantees and attack surfaces
    - KERI Overview (for mudbloods & wizlords) 
    - Drummond will also do a Mugglesfest
    - Kepler IpFS peripheral  Charles Cunningham
    - KERI TELS Smart Contracts Issue VCs, Issue HMI, etc Charles Robert etc
    - GLEIF will hold a session on vLEIs (issued against KERI AIDs)
    - KERI Q&A - interactive sessions (led by Henk)
    - Human Colossos Foundation (HCF) - session on... DRI supply chain? personal data agent?
    - keri-dht-py
    - ? keri agents to DidCom (Ivan Jolocom)
    - [Non-KERI] - ACDC TF (ToIP) Sam Robert 
    - Did:KERI method session (community)  Did:indy:xxx:keri
        - [Indy](https://wiki.hyperledger.org/display/indy) [DID Method](https://github.com/hyperledger/indy-did-method)
    - Community attend DID:PEER working group.
    -   

<details>
<summary>Minutes</summary>

- Indirect Mode Step by SteStep by Ste
    Two stage escrow for events
       stage one is partially signed events.  
       stage two is partially witnessed 
       
       once fully witnesses and signed then becomes first seen.
          must meet both thresholds kt and wt
       
    Validator/Watcher/Juror/Judge (confirmation side) need to be to request replay of event log and latest and any signatures and witness receipt
    Heterogenous  replay from a witness would attach all signatures and receipts from itself and other witnesses.
    Check the witness for current key state to confirm if met witnesss threshold
    
    Controllers responsiblity to push copies of th witness to all its witnesseses.  
    
    Vulnerability rotating witnesse  (see  white paper rotating witnesses section) Witnesses have to witness the to ensure continuity of discover
        witnesses must sign the rotation event that rotates away from them
        new whitepaper - steps to make compromised witnesses point to discovery mechanism for new witnesses temporary forwarding
        KEL includes evetn that rotates them out
        
    Additional optional requirement to added prior witness threshold to first seen. Validator

</details>

## Agenda March 30

Agenda
1. Q&A - SecurityTopics
    2. [Incentives](https://github.com/decentralized-identity/keri/blob/master/docs/Q-and-A-Security.md#q-how-are-keri-witnesses-and-watchers-incentived-to-spread-kels-and-kerls-and-make-them-available)
3. [Pruning or sharding KELs& KERLs](https://github.com/decentralized-identity/keri/blob/master/docs/Q-and-A-Security.md#q-could-a-kel-or-kerl-be-pruned-or-charded)
4. [Safe scaling](https://github.com/decentralized-identity/keri/blob/master/docs/Q-and-A-Security.md#q-how-does-keri-scale-safely-without-comprising-the-security-model)
5. TEL interop with other txn logs - IPFS/Protocol Labs? (WIP/speculative)

<details>
<summary>Minutes:</summary>
* Incentivization question - Q: How are KERI witnesses and watchers incentived to spread KELs and KERLs and make them available?
    - Sam: DNS and other infrastructure generally not billed to end-user; relative cost per end-user substantially lower than traditional/first-gen DLTs and blockchains 
        - Sam: Assumption: Watchers will be comparatively cheap and small communities, networks, and services will likely stand one up as a "loss leader"
        - Sam: Controllers incentivized to stand up witnesses - controllers will likely buy/lease at least 1 witness if they want their AID publishized/diseminated ; cloud-scale infra (2 orders of magn lower than DLT infra)
    - Henk: KERI versus Lightning/BTC Layer2: could witnesses and watchers form tiers or "layers"? Will there be cheap secondary/light-node witnesses and heavy-duty, enterprise-scale witnesses?
        - Sam: Communities and networks will pool resources and security and service models will evolve, we assume
    - Chunningham: Freer market closer to blockchain market model or pay-as-you-go clouds; no real moats or lock-ins in the spec as written...
    - Henk: I'm not really worried about watcher market being distorted
        - Juan: Testability?
        - Chunningham: Implementation guide should maybe go into how to firewall different clients (like VMs on a cloud server) or other security-model eccentricities
        - Sam: duplicity tracking ; Juan: can a conformance test enforce publication of records or logs to judge them fairly as service providers?
            - Sam: maybe but that's layers and layers above the current spec... this spec gives anchors for that kind of tracking, at least? //credit scoring based on opaque algos and unknown data stores and local identifiers - nothing portable to audit, proprietary turtles all the way down...
            - 
        - Sam: Decentralizing REPUTATION was a core driver of decentralized identity in its early days (and core ideological thread in IIW); we could be dogfooding our own decentralized infrastructure reputation; pagerank and star-ranking systems are opaque and difficult to audit; publishing algos should still be our goal, and auditable algos is everything; 
* Pruning and sharding?
    - Pruning <> Tombstoning
    - Sharding = recombinatory P2P replication
            - Chunningham: Every KEL is already shardable because each root identifier could be split, combined, moved whenever
    - Henk: How big is KEL in the worst case scenario or corner case? 
        - Sam: You could chunk or prune huge KERLs; that's overkill unless it's really huge
        - Sam: You can archive the old state and just keep genesis and last year's updates, for ex.
        - Sam: WCS: high-volume millions of SIGNING events per hour is realistic corner case to worry about, however. If each transaction is sealed as a distinct event, that would make for a pretty big KEL... 
            - That might be kind of an anti-pattern tho; implementation guide should probably recommend a merkle every minute in super high-volume signing infrastructures, for example; 
            - WCS KELs are 500bytes per event
            - 10K txns per second = "visa scale"; load balancing may be needed; horizontal scalability achieved by delegation trees; delegations allow segmentation of storage (i.e. pre-sharding); if audit logs are anchored to delegated events in a pre-sharded log, you achieve very good scalability 
* Safe scaling: is everything more secure as more witnesses and more watchers are added?
    - Sam: watchers and witnesses have two separate effects;
        - ambient verifiable requires even distribution (and total coverage) of watchers to detect duplicity; the more, the better
        - enough watchers allow a lower threshold of witnesses that need to stay honest - each controller sets a ratio of witnesses that need to confirm an event, if each of the witnesses is watched enough, the security model is the same (and not improved by more witnesses total) - 
        - Charles: put another way, first few witnesses are exponentially more secure than n-1, but after a few witnesses, each additional witness's security gain approaches zero asymptotically
        - Sam: Controllers' security increased by more witnesses; validator's assurance is increased by more watchers
        - Sam: Controllers needs to do an eclipse attack to fool a validator, which is impossibly expensive with enough watchers
    

</details>

## Agenda March 23

#### Question: Philip Question about Streaming

Philip: Trying to recognize the messages coming in. One of the test failed. It was only sending one message.

##### Answer
Sam: Python is using asynchronously. Py doesn't care the stream ends only that the group ends. So that's interesting.
Q: can we put in the protocol: {what?}

#### Question about whitepaper paragraph 11.3.1 Out-of-order KAACE, last part:
> "An escrow cache of unverified out-of-order event provides an opportunity for malicious attackers to send forged event that may fill up the cache as a type of denial of service attack. For this reason escrow caches are typically FIFO (first-in-first-out) where older events are flushed to make room for newer events."

> "That ordering (in KAACE, ed.) is already provided to the algorithm as an input by the controller." (from 11.3.2)

    Question: How does FIFO prevent effective DOS attacks?
    
##### Answer
If you dont have any loadbalancing, the messages are going to be processed fifo. Only when an attacker has full bandwith available to overload the buffer, they could frustrate the process to get honest messages in.
As soon as you're able to balance the receipt of messages in the buffer, you'll be able to get the right messages (from honest senders) through.


#### Two Questions about Discussion-thread in Slack WG Sidetree
> 1. Dave Huseby: what you're describing is what I call "wedge technology".
wedge technologies are so decentralized that to stop it, the entire internet would have to be turned off. they drive a wedge between the oligarchy and the internet they use to maintain power. either they keep the internet on and the system operates in defiance of whatever rules/lies they promote, or they turn the internet off and lose their primary tool for maintaining power.

    Question 1: Is KERI wedge technology?
    
##### Answer
Each controler gets to decide which infra to use, if they want their own infra everywhere they could do that with KERI.
The answer to centralisation presurre that Dave mentions: if you have enough portability you reduce the ability to lock you in. You need a competive environment. There are some perverse incentives around: The powerful incumbents of **decentralised** initiatives change the rules as they go, which makes it more centralised.
Tip: [Book](https://www.amazon.com/Saving-Capitalism-Capitalists-Unleashing-Opportunity/dp/0691121281): Saving Capitalism From The Capitalists. (some 20yrs old)


> 2. Daniel Buchner: it is if you don't want a centralized set of Location Providers,
who you must trust to be nice and LET you hop to another,
**that's the problem with these Witness/Validator systems: they introduce a trusted intermediary layer**,
I want to be able to say "Come and take it",
in the most blunt, bird-flipping way humanly possible.
Base lineage must be globally observable to avoid trusted rotation intermediaries, 
^ this is an absolute,
There's no way around that fact,
You can't have your cake and eat it too

    Question 2: Is Buchner right about KERI's architecture?

##### Answer
Your witnesses in KERI are *not* under the control of any intermediairy per definition. It’s a choice. And this choice is to be made by the controller. KERI is globally observable because its ambient availability. A validator gets the _signal_ from duplicity detection. And then the controller could indicate what’s going on (if the controller is not maliicious of course). 

This how a `validator` can reconcile with a fallback mechanism (eg. key rotation). KERI does not guarantee liveness of the keystate (example where you have liveliness of key compromise: a btc address and its authorotative key). 

Instead, KERI is a key compromise discovery mechanism. And if there is a compromise, you can send a signal. KERI is all about end verifiability of digital signatures. Digital signatures are legal contracts and it's dependent on the ecosystem governance framework how to avoid liability of the controller for the right key state. KERI does not answer that question. The liable controller can add on several layers in / with KERI to reduce the risk of the controllers liability. The risk that succesfull attacks can occur, can be deminished because they can add extra protection mechanisms.


#### Question raised by Philip: Interested in the roadmap.
Sam: April 20 2021 IIW is coming up. It would be good to have some indirect mode samples.\
Discussed https://github.com/decentralized-identity/keri/issues/108

##### Answer
What is a bare bones version of indirect mode with witnesses. What is the shortest path to basic indirect mode? Answer has been added to [comment]( https://github.com/decentralized-identity/keri/issues/108#issuecomment-804927231)
</details>

#### Q&A discussion https://github.com/decentralized-identity/keri/blob/master/docs/Q-and-A.md#q-how-does-keri-match-the-trust-over-ip-model-and-how-does-keri-fit-in-the-w3c-did-standardization
##### Answer
The ToIP stack has a left side (governance) and the right side (technical)
![](https://i.imgur.com/j8pOkZw.png)

###### Technical
KERI is at lower levels of the ToIP. Other DID methods will add KERI to their method and that's how KERI could be present in these layers.\
The registry has reservered DID:KERI instead of DID:UN\
KERI is non-existing in LAYER 4,  VCs only (layer 3) as content hashpointers in KERI, no native structure for VCs in KERI.

To summarize: Once we talk DID, we already talk about layers above KERI.

###### Governance
In the left side of the ToIP stack we have the liability issues we've already discussed.


## Agenda March 16

Specification hour:
-  replay mode refactor & witness logic
    - basic non-promiscuous mode logic
    -  nonpromiscous owned local vs nonpromiscuous owned non-local
-  Continue discussion on TEL simple vs complex
-  summarize/conclude [Query discussion](https://github.com/decentralized-identity/keri/issues/109)
-  [authentication mechanisms](https://github.com/decentralized-identity/keri/issues/109#issuecomment-797650630) for query protocol
    -  noninteractive universal  
    -  interactive standard http



Development:
- Demo tweaks 
    - python demos updated 
        - Bob demo now requires out of order escrow
        - Sam demo adds more events (but will break if tested against older demo script)
        - logging to /vectors/ in the Py version; verbose b64 logging for now, could be a performant stream
            - annotation could alternate b64-only and non-b64-containing lines to strip out annotations
- Brief updates-- everyone's still working

Misc:
- transaction logs secured by KERI
    - as DID doc updates
    - as smart contracts

<details>
<summary>Minutes:</summary>

Specification hour:
-  replay mode refactor & witness logic
    - def (prom): event processing logic accepts all events (no source filtering/validation)
        - watchers promiscuous by nature/default
        - controllers 
    - basic non-promiscuous mode logic
    -  nonpromiscous owned local vs nonpromiscuous owned non-local
    - steps for moving away from promiscuity: changeable modes
        - each controller privileges the identifier it controls (its own) and has to protect it above all else
            - each controller keeps an authoritative local copy to detect inconsistencies - protecting it from bad events is paramount
            - non-prom local mode: only accept events into a log if it comes via a message the controller signed (with the controlled identifier/keypair)
                - multisig doesn't matter: as long as one of the sigs is yours
                - the log generated this way needs to be accessed locally (and perhaps secured differently?)
        - Normative definition of non-prom mode: NEVER accept an event as first-seen if your key made it and it came non-locally (but maybe put it in the duplicity log for future detection/forensics)
        
    - sidebars:
        - why would you be accepting your own events in the first place? where do they come from?
            - Sam: one common implementation pitfall: multiple copies of authoritative logs
            - Sam: Python's structure to minimize this risk: internal and external events all have to pass through the same validation mechanism, this is similar-- they're you're events, but you want to apply the same process to them as events received from others, and you need to log them before transmitting/publishing them
        - Steve: Terminological observation: "promiscuous" comes from networking design: there, it refers to validating *destination routing* (don't open an envelopes without your name on them); here, we're validating *origin routing*; i see the analogy but this might be confusing to some
        - what's "local interface" mean? you sign events (that come locally) and receipts (that come from other agents); i.e., make sure the controller had the tightest control possible over the event
            - how tight is enough? will vary across minimum accepted degree of security and architecture-- i.e. multiple processors, multiple threads, diff memory control, edge devices, TEE/sec envs, a docker on AWS with observable keystore...
            - this might need to bake a bit-- thinking of implementer guidance or requirements requires thinking through levels of security or attack surfaces
        - 3 modes in KERI and did:peer, configurable with icp config flags
            - pair-wise/direct mode
                - Q: is pair-wise a special case of n-wise, and if so, why have different mode logic for pair-wise?
                    - A: Yes, but just pair-wise has an obvious relationship between 2, without needing a list of participants (just party and counterparty), so no need for the extra config which represents n-wise
                - pair-wise is NOT the same as n-wise with n=2 in terms of config or behaviour
                    - n-wise has different multi-sig requirements for members of the group
            - n-wise/"group mode", would have witnesses as members of a private group which is identified by the KEL prefix
                - would repurpose witness list to represent peers in the group
                    - Q: can we use transferable identifiers for peers in group mode?
                        - A: it creates much greater complexity for validation by requiring lookup and KEL processing of witnesses, potentially with approaching-infinite regress
                    - witness rotation implements group membership change without rotation of witness key pairs/identifiers
                    - ICP of a group lists pubkeys of members participating in multisig
                        - Q: can participants re-using a public ID in group mode lead to correlatability of the "private" ID?
                            - A: group mode should be private and the IDs should not be re-used. group members will collect all IDs for the ICP event, but all info is shared via direct mode (pair-wise is used to bootstrap n-wise). pre-rotated 'nxt' can be calc'd independantly by any group member and the event can be "published" and signed by all members to finalise/commit. In this way, the single-sig of direct mode is used to bootstrap the multi-sig of group mode when the members collect+sign the event data
                        - Q: could a group include a pubkey which is not controlled by any member for some malicious correlative purpose?
                            - A: yes, but a threshold-meeting subgroup would be able to remove it (groups can use multisig to represent their governance model)
            - any-wise/indirect mode
            
            
-  Continue discussion on TEL simple vs complex
    - simple: 3 states for the resource/credential
        - unissued
        - issued
        - issued and revoked
    - complex: arbitrary states/VM state
        - needs some similar features to a KEL: SN, backhashes, state representation etc.
        - can use some similar security mechanisms: first-seen, basic TAACE
        - can either embed TX state in TEL or anchor TX state in TEL
            - state and security model can be separated
        - example: DID Methods
            - transactions in did methods are updates to the DID Doc/state
            - KEL provides the control proof while first-seen applies to the first VERIFIED transaction (TX anchored at a point in a KEL with valid proof of control)
                - transactions are not ordered in a KEL, just the TEL
                - verifiers of TEL transactions must follow the KAACE sec model for the KEL else be duped
        - difference between KEL and TEL: TEL can track value without loss, while a KEL can have loss in the latest transaction state (a rotation which is duplicitous is discarded, the keys in the event are never active)
-  summarize/conclude [Query discussion](https://github.com/decentralized-identity/keri/issues/109)
-  [authentication mechanisms](https://github.com/decentralized-identity/keri/issues/109#issuecomment-797650630) for query 
    - defn of a replay attack:
        - digital sigs allow for non-interactive proof of authentication
        - interactive vs non-interactive: interactive requires presence of authenticator, non-interactive does not (non-interactive is generally better for many reasons)
        - non-interactive proofs can be replayed to any verifier, because the information is "static"/does not change or depend on the particular instance of authentication
        - interactive proofs can include a nonce in the 'request' which is also included in the authenticated response, binding the response to that particular instance of authentication. this challange varies the signed information which requires knowledge of the private key in every instance
        - simple nonce example for interactive query authentication is a datetime stamp, which doesnt need to be generated by the verifier but can be verified as  timely/sufficiently-recent by the verifier
            - monotonicity of datetime stamps allows for simple caching to prevent different types of meddling with nonce-generation (system clock manipulation) on the verifier's side
            - Q: datetime stamps could have issues with clock skew?
                - A: timeliness window can be very large, even a full day, to account for skew, as long as it's still monotonic
    -  noninteractive universal  
    -  interactive standard http
- Multi-sig Issues.
    Group mode.


</details>

## Agenda March 9


Zoom Link: https://us02web.zoom.us/j/81492837711?pwd=OU01ZVpYYmdrcGJDNHhUWU5VNDkxdz09

- [X] [Check prepared answer in Q-and-A](https://github.com/henkvancann/keri/blob/master/docs/Q-and-A-Security.md#q-keri-is-inventing-its-own-key-representation-and-signature-format-why-did-you-do-that)

Specification Hour:

- [kid0003 prefix derivation process update](https://github.com/decentralized-identity/keri/pull/115)
- Query Design Proposal: Feedback on [GH](https://github.com/decentralized-identity/keri/issues/109)
    - Most recent/elaborated version of proposal, synthesizing a LONG thread [here](https://github.com/decentralized-identity/keri/issues/109#issuecomment-791961368)
- Best-practice for historical/post-rotation verifications

Development:

- first seen mode
- seq number mode (replay)
- conjoined mode


<details>
<summary>Minutes: </summary>
***Q: KERI is inventing its own key representation and signature format. Why did you do that?
(@OR13) argues the following:
In order to share code / we would need shared building blocks. Sidetree is built on JWS / JWK. KERI is inventing its own key representation and signature format. These are the lowest level building blocks, so them being different will prevent a lot of potential code reuse.

{TBW prio 2:
- the desire to control the entire stack, and not use anyone else's tooling
    - Kid0001Comment - `multicodec` may not be such a stable standard to be breaking or abandoning...
        - `multicodec` - draft standard, chaotic mix of binary and text-basedd entries in a crowd-sourced registry/table...
            - Sam: most implementers are doing a subset of the chart anyways, making it even more unstable for interop purposes
        - length of item not included in encoding table - incompatible structure (assumed enveloped data structure)
        - composability (via concatenation) for framing
- DID and VC layers are the appopriate layers for interoperability
    - streaming support > interop at signature layer?
- The performance/security goals of KERI drive its design which makes incompatible with Linked Data tooling
    - enveloped data format - signatures have to put on/outside the payload
    - MsgPack and CBOR- work with block-delimited structures
    - JWS/JWK - also enveloped, also incompat with streaming
        - framing events = better streaming support
    
Specification Hour:

- [kid0003 prefix derivation process update](https://github.com/decentralized-identity/keri/pull/115)
- Query Design Proposal: Feedback on [GH](https://github.com/decentralized-identity/keri/issues/109)
    - Seth : a little clarification now might save an hour of GH writing: I was trying to get to default behaviors and optional flags for authoritative-only, get-all
        - DDoS: Flooding a witness with "get-all" requests would be a new DDoS vector, maybe?
        - Sam: two diff replay modes- dups logged separately (in a DEL); a KEL can't have duplicates, DELs can store traces of a recovery/fork-- replay fork events *in order first seen*, then the recovery events that squash the fork
        - monotonic date-time on signed requests --> protect query system itself from replay attacks (if non-interactive)
            - for queries over HTTP, interactive seems a no-brainer; for bare-metal 
    - Most recent/elaborated version of proposal, synthesizing a LONG thread [here](https://github.com/decentralized-identity/keri/issues/109#issuecomment-791961368)

Best-practice for historical/post-rotation verifications
- slides from "newest slide deck" [version 2.58](https://github.com/SmithSamuelM/Papers/blob/master/presentations/KERI_Overview.web.pdf)
    - tripartite data authenticity model versus bipartite model
    - per-VC revocation in tripartite model versus revoke-all
        - kveros, oauth-- revoking key = revoking all tokens derived therefrom (periodic revocation because stale tokens are a security liability)
            - bearer tokens usually managed on [this model](https://findanyanswer.com/how-does-a-bearer-token-work)
        - OCaps uses delegated bipartite model (attenuated caps)

![](https://i.imgur.com/bf7zIIw.png)


- "open loop split model": presentations not trackable by issuer/source 
    - versus "closed loop split model"
    - Charles: smart contract transaction logs? Sam: You bet! Offchain smart contracts?
        - Each state machine (i.e. smart contract), it's own TxnLog
        - Juan: Requirements? All smart contract languages created equal? Sam:...
    - Seth: 
    - peerDID as CRDT - did doc = registry state (microTxnLog)
        - Sidetree in KERI : CRUD ops on did docs would just be txns ("can't build keri in sidetree but can build sidetree on keri")
    - any DID method's primitive operations can be anchored on a transaction log IFF it depends on the KERI security model (would allow for did document operations on did:keri and did:XX:keri)

| Closed Loop | Open Loop |
| -------- | -------- |
| - correlation possible  | + better privacy     |
| + easier   | - more work     |
| - VDR is possible, but disfunctional| + separation of ?  |
       
Development:

SCOIR demos: scripts to walk through a fork and recovery 
- goodguy, badguy, innocent third party; 
    - first seen mode
    - seq number mode (replay)
    - conjoined mode
- Sam: next step: qb4 for binary compression (concat, not envelope/parse)

![](https://i.imgur.com/lIgRKA9.png)


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
