# Q&A about KERI
<img src="../images/Keri_logo_color_on_white.png" alt="KERI logo" border="0" width="300">

**The questions are of a varied level: basic and detailed. The answers are mostly directed towards generally interested people and newbies.**

Why should you read or step through the Q&A? To get a different angle to the same topic: KERI.


```
{TBW} means: to be written
{TBW prio 1} means to be written with the highest priority, 3 = no urgency, 2 = intermediate}
```
- [Q&A about KERI](#qa-about-keri)
    + [Disclaimer](#disclaimer)
    + [List of questions and definitions](#list-of-questions-and-definitions)
  * [Knowledge you should be confidently applying](#knowledge-you-should-be-confidently-applying)
  * [Actions you should be comfortable with](#actions-you-should-be-comfortable-with)
- [Jump table to categories](#jump-table-to-categories)

Inspired by presentation given and questions asked on the [SSI webinar May 2020](https://ssimeetup.org/key-event-receipt-infrastructure-keri-secure-identifier-overlay-internet-sam-smith-webinar-58/), but also issues raised and the progress made, here on Github (Turn on 'Watch' if you want to be notified of conversations).

Beware: A Q&A is always *work in progress*. Tips & help welcome.


### Disclaimer
None of the respondents in the **open** repo and presentations have been explicitly named as a source, except for ***Samuel M. Smith Ph.D.*** and ***@henkvancann***. If there is no reference added to the answers, then it's Samuel M. Smith who answered the question. Most of the editing is done by @henkvancann, which might have introduced ommission, errors, language glitches and such. Sorry for that, feel free to correct by submitting a pull request (PR).\
For practical reasons educational images uploaded by Github members have been downloaded. We de-personalised them by giving images a new name. Under these new names these images have been uploaded to github and used in the Q&A to clarify the questions and answers.

Keri's content is licensed under the [CC by SA 4.0. license](https://creativecommons.org/licenses/by-sa/4.0/). Parts of the video offered on SSI Meetup webinar 58 have been captured and uploaded to Github to support the answers to general questions about digital identity and more in depth answers to question about Keri.

We've done our best to protect the privacy of the Github by investigating the images we used. We haven't come across personal identifiable information (pii). However, should we have made a mistake after all, please let us know and we'll correct this immediately.

### List of questions and definitions

- [Definitions:](#definitions)
      - [Ambient verifiability](./Glossary.md#ambient-verifiability)
      - [Agent](./Glossary.md#agent)
      - [Agency](./Glossary.md#agency)
      - [Autonomic Identifier](./Glossary.md#autonomic-identifier)
      - [Autonomic Namespace](./Glossary.md#autonomic-namespace)
      - [Autonomic idenity system](./Glossary.md#autonomic-idenity-system)
      - [Content-addressable hash](./Glossary.md#content-addressable-hash)
      - [Controller](./Glossary.md#controller)
      - [Correlation](./Glossary.md#correlation)
      - [Cryptocurrency](./Glossary.md#cryptocurrency)
      - [Decentralized Identity](./Glossary.md#decentralized-identity)
      - [Derivation code](./Glossary.md#derivation-code)
      - [Duplicity](./Glossary.md#duplicity)
      - [Entropy](./Glossary.md#entropy)
      - [Establishment Event](./Glossary.md#establishment-event)
      - [End verifiable log](./Glossary.md#end-verifiable-log)
      - [Entity](./Glossary.md#entity)
      - [External consistency](./Glossary.md#external-consistency)
      - [Inception Event](./Glossary.md#inception-event)
      - [Inconsistency](./Glossary.md#inconsistency)
      - [Identity](./Glossary.md#identity)
      - [Internal inconsistency](./Glossary.md#internal-inconsistency)
      - [KERI Agreement Algorithm for Control Establishment](./Glossary.md#keri-agreement-algorithm-for-control-establishment)
      - [Key](./Glossary.md#key)
      - [Key Event Log](./Glossary.md#key-event-log)
      - [Key Event Receipt Log](./Glossary.md#key-event-receipt-log)
      - [Non-Establishment Event](./Glossary.md#non-establishment-event)
      - [Payload](./Glossary.md#payload)
      - [Public Key Infrastructure](./Glossary.md#public-key-infrastructure)
      - [Root of trust](./Glossary.md#root-of-trust)
      - [Seal](./Glossary.md#seal)
      - [Secret](./Glossary.md#secret)
      - [Self Addressing Identifier](./Glossary.md#self-addressing-identifier)
      - [Self Certifying Identifier](./Glossary.md#self-certifying-identifier)
      - [Self Sovereign Identity](./Glossary.md#self-sovereign-identity)
      - [Spanning layer](./Glossary.md#spanning-layer)
      - [Transfer](./Glossary.md#transfer)
      - [Trust-over-IP](./Glossary.md#trust-over-ip)
      - [Validator](./Glossary.md#validator)
      - [Verifiable Credential](./Glossary.md#verifiable-credential)
      - [W3C DID](./Glossary.md#w3c-did)
      - [(Digital Identity) Wallet](./Glossary.md#-digital-identity--wallet)

- [Q&A section General](#qa-section-general)
  * [What is KERI?](#what-is-keri)
  * [Is KERI a DID?](#is-keri-a-did)
  * [Why use KERI?](#why-use-keri)
  * [Who is KERI? Is it a company or a not for profit?](#who-is-keri--is-it-a-company-or-a-not-for-profit)
  * [In what programming languages is KERI available?](#in-what-programming-languages-is-keri-available)
  * [How KERI fit in the 10 principles of SSI by Christopher Allen?](#how-keri-fit-in-the-10-principles-of-ssi-by-christopher-allen)
- [Q&A section KERI operational](#qa-section-keri-operational)
  * [Where can I download KERI?](#where-can-i-download-keri)
  * [Where can we find the code and how could a coder get started?](#where-can-we-find-the-code-and-how-could-a-coder-get-started)
  * [What would you see as the main drawback of KERI?](#what-would-you-see-as-the-main-drawback-of-keri)
  * [How can it be one solution, fit for all SSI problems?](#how-can-it-be-one-solution--fit-for-all-ssi-problems)
  * [Where you would need something quite different than KERI?](#where-you-would-need-something-quite-different-than-keri)
  * [How does KERI scale](#how-does-keri-scale)
  * [How are KERI witnesses and watchers incentived to spread KELs and KERLs and make them available?](#how-are-keri-witnesses-and-watchers-incentived-to-spread-kels-and-kerls-and-make-them-available)
  * [How to handle multiple formats of KEL and KERL through time. Will they be backwards compatible?](#how-to-handle-multiple-formats-of-kel-and-kerl-through-time-will-they-be-backwards-compatible)
  * [Could a KEL or KERL be pruned or charded?](#could-a-kel-or-kerl-be-pruned-or-charded)
  * [How to bootstrap KERI on the internet? Is it like fax machine; the more there are the more effective it is?](#how-to-bootstrap-keri-on-the-internet--is-it-like-fax-machine--the-more-there-are-the-more-effective-it-is)
  * [Why does KERI demand signing and digesting the full over-the-wire serialization of a message?](#why-does-keri-demand-signing-and-digesting-the-full-over-the-wire-serialization-of-a-message)
  * [What does KERI look like?](#what-does-keri-look-like)
  * [Is there a KERI course or webinar available?](#is-there-a-keri-course-or-webinar-available)
  * [Could Keri work for edge computers that need self sovereign identity? How to (selectively) share control over the `SCI`/`SAI` with the owners of the device?](#could-keri-work-for-edge-computers-that-need-self-sovereign-identity--how-to--selectively--share-control-over-the--sci---sai--with-the-owners-of-the-device)
- [Q&A section Root of trust](#qa-section-root-of-trust)
  * [What do I need to trust in KERI?](#what-do-i-need-to-trust-in-keri)
    + [What is the difference between a trust basis and a trust domain?](#what-is-the-difference-between-a-trust-basis-and-a-trust-domain)
  * [KERI does not need a blockchain, but how does it establish the root-of-trust that we need for SSI? How does the data persist?](#keri-does-not-need-a-blockchain--but-how-does-it-establish-the-root-of-trust-that-we-need-for-ssi--how-does-the-data-persist)
- [Q&A section Why the internet is broken](#qa-section-why-the-internet-is-broken)
  * [Why would the internet be broken?](#why-would-the-internet-be-broken)
  * [How can the internet be fixed?](#how-can-the-internet-be-fixed)
  * [What's wrong with SSL certificate intermediairies?](#what-s-wrong-with-ssl-certificate-intermediairies)
  * [What's DNS Hijacking](#what-s-dns-hijacking)
  * [What is 'platform locked trust' and why should we bother?](#what-is--platform-locked-trust--and-why-should-we-bother)
  * [How to repair the internet trust layer?](#how-to-repair-the-internet-trust-layer)
  * [What role does KERI play in the suggested "repair of the internet"?](#what-role-does-keri-play-in-the-suggested--repair-of-the-internet)
- [Q&A section Identifiers](#qa-section-identifiers)
  * [How is a KERI identifier different than a regular identifier in DID methods?](#how-is-a-keri-identifier-different-than-a-regular-identifier-in-did-methods)
  * [Is my KERI identifier public?](#is-my-keri-identifier-public)
  * [Is a KERI identifier GPDR proof?](#is-a-keri-identifier-gpdr-proof)
  * [What do I need a self-certifying identifier for?](#what-do-i-need-a-self-certifying-identifier-for)
  * [What do I need a self-addressing identifier for?](#what-do-i-need-a-self-addressing-identifier-for)
  * [What do I need a multi-sig self-addressing identifier for?](#what-do-i-need-a-multi-sig-self-addressing-identifier-for)
  * [What do I need a delegated self-adressing identifier for?](#what-do-i-need-a-delegated-self-adressing-identifier-for)
  * [What do I need a self-signing identifier for?](#what-do-i-need-a-self-signing-identifier-for)
- [Q&A section Event logs](#qa-section-event-logs)
  * [What is a Key Event Log?](#what-is-a-key-event-log)
  * [Why is a Key Event Log crucially important?](#why-is-a-key-event-log-crucially-important)
  * [How do I create a KEL?](#how-do-i-create-a-kel)
  * [How can I trust a KEL?](#how-can-i-trust-a-kel)
- [Q&A section Inconsistency and duplicity](#qa-section-inconsistency-and-duplicity)
  * [What kind of Inconsistencies do we have?](#what-kind-of-inconsistencies-do-we-have)
  * [What is Duplicity?](#what-is-duplicity)
  * [Why should we care about Duplicity?](#why-should-we-care-about-duplicity)
- [Q&A section Key rotation](#qa-section-key-rotation)
  * [What is Key Rotation?](#what-is-key-rotation)
  * [Why bother about key rotation?](#why-bother-about-key-rotation)
- [Q&A section KEL and KERL](#q-a-section-kel-and-kerl)
  * [What the difference between KEL and KERL?](#what-the-difference-between-kel-and-kerl)
- [Q&A section Wallets](#qa-section-wallets)
  * [Why do I need a wallet for KERI?](#why-do-i-need-a-wallet-for-keri)
  * [How can I backup the KERI identifiers in my wallet?](#how-can-i-backup-the-keri-identifiers-in-my-wallet)
  * [Can I receive crypto money in my KERI wallet?](#can-i-receive-crypto-money-in-my-keri-wallet)
  * [Does a KERI wallet store virtual credentials connect to my identifiers?](#does-a-keri-wallet-store-virtual-credentials-connect-to-my-identifiers)
- [Q&A section Signatures](#qa-section-signatures)
  * [Who can sign off my proofs and identifiers?](#who-can-sign-off-my-proofs-and-identifiers)
  * [What is the practical use of signatures?](#what-is-the-practical-use-of-signatures)
  * [Do verifiers, validators, witnesses and watcher sign off `payloads`?](#do-verifiers--validators--witnesses-and-watcher-sign-off--payloads-)
- [Q&A section Proofs](#qa-section-proofs)
  * [What does KERI proof?](#what-does-keri-proof)
  * [Does KERI know whether any message in the Event Logs are valid or true?](#does-keri-know-whether-any-message-in-the-event-logs-are-valid-or-true)
  * [How can we verify that a statement by a controller is valid?](#how-can-we-verify-that-a-statement-by-a-controller-is-valid)
  * [How can we trust what was said or written?](#how-can-we-trust-what-was-said-or-written)
- [Q&A section Private Key Management](#qa-section-private-key-management)
  * [Not your keys, not your identity?](#not-your-keys--not-your-identity)
  * [The wallet is there to store my KERI private keys safely, no?](#the-wallet-is-there-to-store-my-keri-private-keys-safely--no)
  * [Are compound private keys (Shamir Secret Sharing) and multisignature schemes possible to incept identifiers?](#are-compound-private-keys--shamir-secret-sharing--and-multisignature-schemes-possible-to-incept-identifiers)
  * [How to delegate control over my private keys that control my identifiers?](#how-to-delegate-control-over-my-private-keys-that-control-my-identifiers)
- [Q&A section Blockchain](#qa-section-blockchain)
  * [Does KERI use a blockchain?](#does-keri-use-a-blockchain)
  * [What's the difference between KERI and blockchain?](#what-s-the-difference-between-keri-and-blockchain)
  * [Why not register identities on an open public ledger like bitcoin, ethereum or soverin?](#why-not-register-identities-on-an-open-public-ledger-like-bitcoin--ethereum-or-soverin)
- [Q&A section Agencies](#qa-section-agencies)
  * [How can KERI offer consistent services and truth?](#how-can-keri-offer-consistent-services-and-truth)
- [Q&A section Witness](#qa-section-witness)
  * [Witnesses have no skin in the game, it’s a `nothing at stake` situation, no?](#witnesses-have-no-skin-in-the-game--it-s-a--nothing-at-stake--situation--no)
  * [As long as witnesses keep lying together no one will ever be able to prove them wrong?](#as-long-as-witnesses-keep-lying-together-no-one-will-ever-be-able-to-prove-them-wrong)
- [Q&A section Watchers](#qa-section-watchers)
  * [How can we detect duplicity? Suppose controller has power over witnesses.](#how-can-we-detect-duplicity--suppose-controller-has-power-over-witnesses)
- [Q&A Virtual Credentials](#qa-virtual-credentials)
  * [Why doesn't KERI use certification as a root of trust?](#why-doesn-t-keri-use-certification-as-a-root-of-trust)

<small><i><a href='http://ecotrust-canada.github.io/markdown-toc/'>Table of contents generated with markdown-toc</a></i></small>

## Knowledge you should be confidently applying
- The definitions in the [glossary](./Glossary.md)
- Public private key pairs
- Hashing and hashes
- Signatures
- Bitcoin Improvement Protocols: BIP32, BIP39, BIP44, BIP47, BIP49, BIP84, BIP174
- hierarchical deterministic derivation paths
- Base58
- Eliptic curves
- Blockchains, open public, private and hybrid
- W3C DIDs
## Actions you should be comfortable with
- Amend knowledge and keep existing knowledge up to date
- create a key pair safely and back it up safely
- sweep to a new wallet

# Jump table to categories
- [General](#qa-section-general)
- [KERI operational](#qa-section-keri-operational)
- [Root of trust](#qa-section-root-of-trust)
- [Why the internet is broken](#qa-section-why-the-internet-is-broken)
- [Identifiers](#qa-section-identifiers)
- [Event logs](#qa-section-event-logs)
- [Inconsistency and duplicity](#qa-inconsistency-and-duplicity)
- [Key rotation](#qa-key-rotation)
- [KEL and KELR](#qa-section-kel-and-kerl)
- [Wallets](#qa-section-wallets)
- [Signatures](#qa-section-signatures)
- [Proofs](#qa-section-proofs)
- [Private Key Management](#qa-section-private-key-management)
- [Blockchain](#qa-key-blockchain)
- [Agencies](#qa-key-agencies)
- [Witness](#qa-section-Witness)
- [Watchers](#qa-section-watcher)
- [Security Guarantees](#qa-security-guarantees)
- [Virtual Credentials](virtual-credentials)


# Q&A section General

## What is KERI?
Key Event Receipt Infrastructure; a secure identifier overlay for the internet.

## Why use KERI?
Because there is no secure universal trust layer for the internet, currently (2020).\
KEI is both privacy preserving and context-independent extensible. That means KERI is interoperable accross areas of application on the internet. It does so securely, with minimal sufficient means.\
_(@henkvancann)_

## Is KERI a DID?
`KERI` is not a `DID` method. The proposed related `DID` method is [`did:un`](https://github.com/decentralized-identity/keri/blob/master/did_methods/un.md). A session at the recent **IIW31** presented by Jolocom’s *Charles Chunningham* examines overlap between data models of DID documents and `KERI` identifiers [here](https://jolocom.io/blog/as-seen-at-iiw31-keri/).\
However there are also votes for `did:keri`: _Drummond Reed_ (Dec 2 2020): "at IIW we asked that question and  feedback overwhelmingly favored did:keri. Furthermore, I’ve proposed that the keri namespace be reserved within the method-specific ID spaces of other DID methods as well, The Indy community has agreed to reserve the keri namespace in the Indy DID method."\
_(@henkvancann)_

## Some say that with KERI, a DID can be reduced to did:<identifier>. But that’s not a valid DID?!
_Every DID must have a method name component before the method-specific ID._

The first paper mentioning the absence of the method is [Thinking of DID? KERI On](https://humancolossus.foundation/blog/thinking-of-did-keri-on) by The Human Colossus Foundation, written by Robert Mitwicki. He addressed the concern in the question (the invalidity of the DID method) and made it more clear what the Foundation meant by that: "We look into the future and with that view we think that namespace could be dropped and we could keep only identifier, as the namespace seems to be one of the major drawbacks of decentralized identifiers at the moment. In my opinion `did:keri:<identifiers>`  would be just intermediate step as the issue addressed by post would still hold. We see that KERI could be a major upgraded for DID; not replacement."

## Is it possible to create a KERI DID that is permanently locked to the "did:key" style / ephemeral?
It is. Sections 2.2.3 - 2.3.1 of the [white paper](https://github.com/SmithSamuelM/Papers/blob/master/whitepapers/KERI_WP_2.x.web.pdf) explains transferrability and the "basic"-type identifier, which always represents a public key and may be either transferrable (can be updated) or non-transferrable (ephemeral/did:key style). section 14.2 actually details how these are encoded, basically check the first few chars of the identifier.\
_(CharlesCunningham)_

## DID data model supports verification methods which are not based on public keys or even any cryptography at all. KERI can't do this? 
_In many ways KERI is "better" than DIDs, especially when it comes to proof-of-control. But I think this is one thing that DIDs can do that KERI can't: verification methods which are not based on public keys or even any cryptography at all._

KERI can support them, with some special event type, they use it to store CRDT ops.\
(_@OR13b_)
The point of KERI is to maintain to control of key-derived identifiers. It's not intended to provide all the capabilities of DID.\
(_@_stevetodd__)

## How do I find all the DIDs that stand for apps, code modules, public businesses, and other entities that benefit from being publicly discoverable on a decentralized deterministically iterable registry?
_How might one build a decentralized deterministically iterable registry for such use cases where the entries are securely known to be from the matching Identifier?_\
_The reason I am asking is to get people to think about the system they'd inevitably need to create to support the 95% of use cases (given 95% of identity interactions are between personas of people, places, and things that are discoverable)_\
_Is it not a helpful exercise to game out the things required to support 95% of DID use cases with other DID system developers?_

It's considered a privacy property of KERI, that you cannot enumerate all identitiess, in the same way that finding all minorities of certain religious preference might not be a feature.\
(_@OR13b_)

Discovery is a layer on top of what KERI provides. KERI doesn't preclude DID, nor does it need to implement all of DID. KERI will participate in the DID ecosystem. (_@_stevetodd__)\
It doesn't need/want to solve/serve that slice of the use case pie.

#### Follow up question 1: Why does KERI rule out 95% of the DID-based use cases upfront, where we need public discoverability on a decentralized deterministically iterable registry?
```
The vast majority of users use apps and services that are exchanges between or about the well-known, 
publicly resolvable registered persona DIDs of people, places, or things? 
Let's list a few to see how much of human digital life it covers:
- All social media: Twitter, Facebook, Instagram, Telegram, Signal, etc.
- All public content creation: YouTube, SoundCloud, Spotify, etc.
-All current registries: NPM, all app stores, all things that use those registries 
    (basically every piece of software on the planet)
- All publicly registered objects: cars, boats, airplanes, etc.
Put it this way: very few use cases on this planet will not directly, or within them, 
rely on publicly iterable, globally registered persona DIDs. 
But that said, I'm interested in hearing other opinions or counter arguments to the contrary.
(_@csuwildcat_)
```
*There is an implicit need for the registry to track its entries as DIDs. I guess those 95% use cases will have to get other types of DIDs for that?*

It's possible to make a DID doc that represents a KERI identifier. If you want to resolve it, you can put it in any number of blockchains. That just publishes it. However, they don't have to be published to work. \
(_@_stevetodd__)

Or for example TOR hidden services, these are not designed to be discoverable. In fact, the whole point of tool is to provide anonymity. Anonymity is a property of set membership, and it's destroyed by making the sets small or enumerable.
(_@OR13b_)

 In many scenarii, what the elaborate question explains makes sense. I can understand a different design goal/priority for KERI, I think the rationale is quite clear in terms of where it stands in the DID space.
(_@fimbault_)

#### Follow up question 2: That's not deterministic?! 
_You can't have Registry A magically just trust that a DID from Other System B, it would need to be native to it?_
_Any registry with deterministically resolvable entries requires the entry controllers' IDs and resolutions be native to it. That's an empirical computer science wall type of requirement._ \
_Imagine I want to register a DID in a decentralized deterministically iterable registry - something anyone can run and deterministically know all entries registered with it, wherein the registry has no central entities or authorities that determine the bindings between entries and those who control them..._\
**_Nowhere in any paper on this planet is this a solved problem, because it's basically NP hard_**

It depends on what you mean by resolve. The [white paper](https://github.com/SmithSamuelM/Papers/blob/master/whitepapers/KERI_WP_2.x.web.pdf) explains the points brought up in this question.
(_@_stevetodd__)

{TBW prio 1}


## Nowhere in any paper on this planet is this a solved problem, because it's basically NP hard

Orie Steele (Transmute)  12:30 AM
its considered a privacy property of KERI, that you cannot enumerate all identitiess
## Why do you reinvent blockchains and claim it's something new?
To begin with KERI has no blockchain, and doesn't depend on blockchains. If an implementation of KERI depends on blockchains at all, KERI operates blockchain agnostic.
Secondly KERI doesn't support a crypto currency. It doesn't need currency because it can easily connect to one, if needed. And again, KERI is crypto currency agnostic while doing so.
Lastly KERI is fundamentally different from blockchains like Ripple (Permissioned PBFT consensus) or Stellar (imcomplete open public, non-permissioned PBFT consensus): it doesn't need **total ordering**, timestamping and Proof of Authority consensus on transactions registered on a ledger.

It's comparing apples and oranges. But we're happy to do that exercise for the hard-to-convince part of the SSI community.

```
KERI is nothing like we already know of. It's a mixtures of things. 
You can't say _"Oh, KERI lays eggs, so it must be a reptile"_ It's not a reptile. 
And then you go _"I see, but it gives birth, so it must be a mammal"_. 
It's also not a mammal. It's KERI. 
It may have the characteristics you describe, but it's a species of its own.
(_SamMSmith_)

```
#### How can you get away with not complying to the security model (and guarantees) of an open public blockchain?
KERI better fits the Identity space. Doing away the total ordering in blockchains is a huge performance - and throughput gain, plus less worry about goverance. There's also not such a thing as consensus forks.
KERI solves (or _"gets away with"_ if you wish) this with duplicity detection. Watchers are all that matter. They garuantee that logs are immutable by one very simple rule: **"first seen wins"**.


#### Differences between blockchain-based security and KERI security
- Where KERI doesn't need total ordering in its logs, blockchain do need that. What KERI needs is watchers that construct string of event in the relative order of reception of the KEL  {TBW please explain or improve this: what is this, why is it important?}
- Another characteristic is that KERI identifiers are transferable and blockchain-based identifiers are not, they are bound to their ledger.


## Is it fair to say that DID resolution in general is a security weakness and then push forward KERI in that name? 
_Although some DIDs have not kept up with design goals* of DIDs, e.g. did:web, it is too strong to state this in general. It simply depends on the DID method?\
*decentralization, persistence, cryptographic verifiability._

In brief: we argue that the chain is as strong as its weakest ring.

Security is not build into the protocol but indeed as the eloborate question mentions, it depends on the DID method. Which overall is a huge risk for community as people needs to know the security level which each did method brings. From that perspective without unified security model brings us to the similar situation where, me having private email server in the basement to avoid spying by google, I send out my e-mail to you having it on gmail. I have high security and privacy but other side have just security without privacy. The outcome is that security model is applied in wrong place and KERI aims to fix it.\
_(RobertMitwicki)_

## Isn't it a bit arrogant of KERI to say "my new DID method is so good that it can replace all others for all eternity"?
_But by doing that you will also exclude a lot of existing identifier infrastructure._

I am not denying existence of existing DID infrastructure, but I agree a lot of them could be obsolete if we introduce KERI. A lot of business models which are build upon current model would be obsolete. I understand that a lot of people would not like that, but that is called progress.\
_(RobertMitwicki)_

## Because the DID data model theoretically allows DID methods and verification methods that may NOT be based on cryptographic keys, KERI is capable of spanning all DIDs?

We would like to see some examples of verification methods that are not based on cryptographic keys and are in the scope of DID. The KERI community would like to learn more about these methods. 
It's true KERI is all about cryptographic commitment. But KERI can also support hashed based identifiers e.g. a fingerprint of the content as unique identifier, without the control part.

## Could we see a `WASM` module in the near future for Sidetree and DID:peer interoperability?
 WASM is certainly on the roadmap, but for the main issue of Sidetree and did:peer interop, see the [core KERI spec repo issue](https://github.com/decentralized-identity/keri/issues/79) for more info.\
_(CharlesCunningham)_

## How does KERI match the `trust-over-ip` model and in the `W3C DID standardization`?
[Trust-over-IP](#trust-over-ip):
- Its goal is to be the missing authentication layer of the internet. That's a pretty well matching objective.
- Layer 1 (settlement layer): Where other `DID`s use blockchains or databases to register identities and settle 'transactions' between between, `DDO`s, and `VC`s, KERI uses homegrown native structures: `KEL` and `KERL`.
_(@henkvancann)_
- Layer 2 (communication layer): Non existing in KERI, because KERI is end-verifiable. KERI can use any other means of communication between actors in the ecosystem
- Layer 3 (transaction layer): Since KERI focuses on the more fundamental part of authentication for the internet, you won't find matching functionality for usual trust-over-IP transaction like VCs or money.
- Layer 4 (application layer): {TBW}
_(@henkvancann)_

[W3C DID](https://www.w3.org/TR/did-core/):
1. The KERI developers provisionally design DID:UN, which might become a mixture of DID:KEY, DID:PEER, and DID:WEB, combinable with more functional DIDs in the Identity spectrum DID:SOV, DID:ETHR, etc.
2. No verifiable credentials
_(@henkvancann)_

## Why use KERI?
Because there is no secure universal trust layer for the internet, currently (2020).

## What problem is KERI solving? How? And why can't it be solved by other solutions?
KERI solves the problem of **secure attribution to identifiers**. By ambient availability of verifiable Key event Logs that prove authoritive control over identifier's private keys. It can't be solved by onther solutions known so far because those solution have not managed to span identifier interoperability over the internet.
_(@henkvancann)_
{TBW prio 1}

## Who is KERI? Is it a company or a not for profit?
KERI sits under the *Decentralized Identity Foundation*, [DIF](https://identity.foundation), and within that in the *Identity and Discovery* Workgroup.
Due to its licensing structure, KERI isn't owned by anyone and everyone at the same time. The Intellectual Property Right of KERI is hosted with `DIF`. It is an open source project.

On github KERI is - and will become even more - a thickening bunch of repositories:
 1. https://github.com/decentralized-identity/keri 
 2. https://github.com/decentralized-identity/keripy
 3. etc

 Lastly, the important man, who founded KERI is *Samuel M. Smith Ph.D.*, operationing from his firm [prosapien.com](https://www.prosapien.com).
 _(@henkvancann)_

## In what programming languages is KERI available?
In Python. It will be available in the coming year in Rust, Javascript and Go (2020).
_(@henkvancann)_

## How KERI fits in [the 10 principles of SSI](https://medium.com/metadium/self-sovereign-identity-principle-6-portability-4a7105dd0381) by Christopher Allen?
KERI is not primarily about self-sovereign identity. KERI is primarily about autonomic identifiers, AIDs. That is: identifiers that are self managing. KERI provides proof of control authority over the identifier. What one does with the identifier is not constrained by KERI. But because the primary root of trust of an AID is a KEL which can be hosted by any infrastructure, any identity system (SSI or otherwise) built on top of KERI may also be portable.\
So in my opnion portability of the associated identifiers is essential to any truly self-sovereign identity system.\
(_SamMSmith_)

Where Christopher Allen is talking about *portability of information* related to the identity, in KERI we take this a step further with the *portability of the identifier itself* with respect to its supporting infrastructure (aka spanning layer).  Most `DID` methods do not have portable identifiers. They are locked to a given ledger.\
(_SamMSmith_)

## Does KERI cooperate with other projects in the self-sovereign Identity field?
Yes, KERI sits under the *Decentralized Identity Foundation*, [DIF](https://identity.foundation), and is part of the *Identity and Discovery* Workgroup. There are also non-formal relation with the newly launched trust-over-ip foundation, and there's good reasons to fit KERI into trust-over-ip.\
(_SamMSmith_)

## What's the difference between a `normative` and `non-normative` description or theory?
See the [definitions](#normative) section for what both terms mean. For example, theories of ethics are generally `normative` - you should not kill, you should help that person, etc. Economics is most commonly `non-normative` - instead of asking “how should this person choose which goods to buy?”, we are often more interested in “how does this person choose which commodities they buy?”.

## What's the difference between the KERI whitepaper and the KIDs
The [whitepaper](https://github.com/SmithSamuelM/Papers/blob/master/whitepapers/KERI_WP_2.x.web.pdf) is the historically grown and expanded design document of `KERI`.

A [KID](../kids) is focussed on Implementation; "this is how we do it"  We add commentary to the indivudual KIDs that elaborate on the why. It has been split from the _how_ to not bother implementors with the _why_.

## KERI has invented its own key representation and signature format. Why not conforn to current standards already available?
{TBW prio 1}

## In the KERI system design trade space you strike out features, so you must have stroked out application space too; which?
<img src="../images/trade-space-limitations.png" alt="trade-space-limitations" border="0" width="300">
{TBW prio 2}

# Q&A section KERI operational

## Where can I download KERI?
On (sub)page(s of) [github](https://github.com/decentralized-identity/keri).

## Where can we find the code and how could a coder get started?
The homepage on github [README.md](../README.md) pretty much sums up all the possibilities to download the available code and how developers can currently engage in the development process. We welcome all help we can get.

## What would you see as the main drawback of KERI?
Its main drawback is that it's nascent. (_SamMSmith_)\
KERI is inventing its own lowest level building blocks. That will prevent a lot of potential code reuse. (@OR13)


## How can it be one solution, fit for all SSI problems? 
KERI uses plain old digital signatures from `PKI`, intentionally, so that it may be truly universally applied. KERI solves that hard problem of PKI, that is, key rotation in a standard way. Without a standard way of addressing key rotation, there is no interoperability between systems, they break when you rotate keys because no one knows how to verify the key rotation was done properly. `KERI` solves that problem.\
(_SamMSmith_)

## Where you would need something quite different than KERI?
`KERI` does one thing, it establishes control authority using verifiable portable proofs that are `KEL`s.\
(_SamMSmith_)

## How does KERI scale
`KEL`, `KERL` and `KAACE` might well be very lean alternatives to blockchain based solutions. The hard part is the ambient verifiable architecture.\
 _(@henkvancann)_

## Will KERI be interoperable with DID;peer and Sidetree?
**(@OR13) argues the following:**\
Afaik this ship sailed when KERI decided to define its own event format. I don't think KERI shares any commonality with sidetree or did peer, and it's no longer possible to align them, so while you can start with the same key material, doing similar operations will very quickly result in totally different event structures.

I don't see a way for KERI events to be used by anything but KERI for now, certainly not Sidetree. In the future did:peer might use KERI events directly, but then did:peer would not be Sidetree compatible...

In order to share code / we would need shared building blocks. Sidetree is built on JWS / JWK. KERI is inventing its own key representation and signature format. These are the lowest level building blocks, so them being different will prevent a lot of potential code reuse.

The upside is that KERI could be much better than things built on JOSE. The down side is KERI won't be possible to implement with off the shelf JOSE crypto. Having spent a lot of time with linked data, It looks like KERI is setup to feel all the same kind of pain, regarding reinventing the wheel instead of starting with compatibility with JOSE.

There was also a potential for KERI to align with Ceramic / IPFS / IPLD, but that door closed when the KERI WG decided to reinvent multicodec.

I predict a few years from now we will have:

A. JOSE / JWS / JWK / jose based DIDs\
B. Multicodec / IPFS / IPLD / DAG_CBOR / JWS / JWK / ipld based DIDs\
C. Linked Data / JSON-LD / CBOR-LD / linked data based DIDs\
D. KERI / KERI keys / KERI signatures / keri event log based DIDs

There will be some overlap, for example KERI based DID Documents will likely support JWKs if they want to be useful with any legacy system, but internally KERI will use a different key representation. Similarly sidetree based dids will likely support linked data proofs but will only rely on JWS / JWK for internal operations.

As far as I know, the KERI design has specifically chosen not to build on JOSE, IPLD. or JSON-LD / CBOR-LD. So there won't be any opportunity for interop with KERI below the DID Document layer. Which is true of many other systems, including Ethereum, Bitcoin, Hyperledger based DIDs. Many of which don't share event log interopability.

Imo, if KERI used IPLD / JSON-LD / CBOR-LD, it would be better. Because not using them means reinventing the parts of them that are needed... which comes with the potential for better performance at the cost of inventing a faster wheel, and failing to pull developers / tooling from those established communities. However I can understand the desire to control the entire stack, and not use anyone else's tooling.

From an engineering management and interopability perspective, I would have decided to break compatibility after the whole system was built and working, and only in the areas where JWS / JWK or IPLD performance, documentation or library support was so bad it was justified.

...  We should target interop between KERI and Sidetree at the DID Core and VC Data Model layer.\
**End of (@OR13)'s plea.**

The DID and VC layers are the appopriate layers for interopability. The performance/security goals of KERI drive its design which makes incompatible with Linked Data tooling.\
(_SamMSmith_)
## How does KERI keep identifiers secure?
By the mechanism of availability, consistency, and duplicity.\
We have to handle `race conditions` too, just like any other distributed database or blockchain.\
(_SamMSmith_)

## Is the KERL technically a blockchain/hashed data log, rather than a ledger that implies a balance?
Yes a KEL/KERL is a hash chained data structure. But not merely hash chained but also signed, so its also a cryptographic proof of key state.\
It is not tracking balance it is tracking key state.
(_SamMSmith_)

## Is KERI post-quantum secure?
In brief: yes, pre-rotation with hashed public keys and strong one-way hash functions are post-quantum secure.

Post-quantum cryptography deals with techniques that maintain their cryptographic strength despite attack from quantum computers. Because it is currently assumed that practical quantum computers do not yet exist, _post_-quantum techniques are forward looking to some future time when they do exist. A one-way function that is post- quantum secure will not be any less secure (resistant to inversion) in the event that practical quantum computers suddenly or unexpectedly become available. One class of post-quantum secure one-way functions are some cryptographic strength hashes. The analysis of D.J. Bernstein with regards the collision resistance of cryptographic one-way hashing functions concludes that quantum computation provides no advantage over non-quantum techniques.\
Strong one-way hash functions, such as 256 bit (32 byte) Blake2, Blake3 and SHA3, with 128 bits of pre-quantum strength maintain that strength post-quantum.\
[Source: whitepaper page 65](https://github.com/SmithSamuelM/Papers/blob/master/whitepapers/KERI_WP_2.x.web.pdf)

## According to the SSI Book KERI will never be able to substitute the internet conventional PKI infra. Right?
[SSI Book](https://livebook.manning.com/book/self-sovereign-identity/chapter-8/v-9/144): "As powerful as this (read KERI-like) solution appears, completely self-certifying identifiers have _one major Achilles heel_: the controller’s identifier needs to change every time the public key is rotated. As we will explain further in Chapter 10 on decentralized key management, key rotation—switching from one public/private key pair to a different one—is a fundamental security best practice in all types of PKI. Thus the inability for self-certifying identifiers alone to support key rotation has effectively prevented their adoption as an alternative to conventional PKI.

{TBW prio 1}

## What happens if I or other people are offline?
Any controller can install a Service/Agent Log, controlled by them.

## How are KERI witnesses and watchers incentived to spread KELs and KERLs and make them available?
{TBW prio 2}
## How to handle multiple formats of KEL and KERL through time. Will they be backwards compatible?
{TBW prio 2}
## Could a KEL or KERL be pruned or charded?
{TBW prio 2}
## How to bootstrap KERI on the internet? Is it like fax machine; the more KELs there are, the more effective it is?
Any subject / controller can start creating KERI events in a KERI event log. Dependent of the objectives a controller has with KERI a more peer-to-peer (one-to-one) approach or contrary to that a one to many approach. In the latter case a set of witnesses and their services can emerge per controller. Subsequently one or more verifiers (and their watchers) can also enter the play.
The more entities are getting used to play the different KERI specific roles the more rapid and easy will the bootstrapping / flooding of KERI on the internet evolve.
{TBW prio 1}

## Why does KERI demand signing and digesting the full over-the-wire serialization of a message?
The discussion of `KERI`s approach to *serializing messages and signing and digesting the full over-the-wire serialization* is inconvenient for implementers. The motivation for this approach I am calling Zero Message Malleability as a property of `KERI`. 
This is a "best practices" security first approach that prevents semantic leakage over time that becomes a transaction malleability vulnerability. Indeed `KERI` approach trades off some inconvenience in serialization for better security and reduces the inconvenience of needed to have tightly specified semantics to prevent transaction malleability.\
(_SamMSmith_)

## If the KERI resolver "relies on a distributed hash table (DHT) algorithm .. such as IPFS or GNUnet", isn't that a huge contradiction in terms?! 
_If KERI has this built-in reliance, then doesn't that contradict and defeat the whole purpose of KERI?_

KERI resolver - due to the KERI architecture we get rid of the "magic box" in a way that I don't have to trust any infrastructure component. `DHT` is just example how this can be done in decentralized fashion.\
But the point is that **I don't have to trust any node or network** that the statement is correct. I can cryptographically verify that everytime with KERI. Compare to current DID infrastructure where I have to trust resolution process in each DID-method because as soon as would get DID Document, I can't verify that this is the correct one. Think of it like `DID:peer` where I can always be 100% sure that the `DDO` which I have belongs to that DID. Not every DID method has this kind of properties. And I think this characteristic is crucial for adoption of DIDs.
(_RobertMitwicki_)

## What does KERI look like?
Currently `KERI` is just code, that can be tested and executed in a terminal on the command line. Private key management of KERI will look like `wallets`.\
Key Event Logs (`KEL`) and Key Event Receipt Log (`KERL`) are files with lots of encrypted stuff in there.\
_(@henkvancann)_

## Is there a KERI course or webinar available?
The [SSI Meetup](https://ssimeetup.org/key-event-receipt-infrastructure-keri-secure-identifier-overlay-internet-sam-smith-webinar-58/) webinar on KERI took place in May 2020 and is a good lesson and source of information.\
_(@henkvancann)_

## Could KERI work for edge computers that need self sovereign identity? How to (selectively) share control over the `SCI`/`SAI` with the owners of the device?
Delegation could be used. There is an [issue about IoT](https://github.com/decentralized-identity/keri/issues/54) key and identifier management with `KERI` that answers this question profoundly.\
(_SamMSmith_)

## Delegations in many systems are unilateral. KERI has cooperative delegation. What is that and why is it better?
In many system unilateral delegation is a single point of failure. if a delegated key's delegator gets compromised, you have no way to recover. 

Keys are in different infrastructures in KERI. Both the delegator and the delegatee have keys they manage. If one of them get compromised or lost, we still can recover. Each level of delegation allows delegation of the level above.
_(@henkvancann)_

# Q&A section Root of trust

## What do I need to trust in KERI?
Primary root of trust is KEL not secondary (starts with self cert ID), but then after first rotation if any must have KEL.\
(_SamMSmith_)

### What is the difference between a trust basis and a trust domain?
A trust basis binds controllers, identifiers, and key-pairs.

A trust domain is the ecosystem of interactions that rely on a trust basis.

## KERI does not need a blockchain, but how does it establish the root-of-trust that we need for SSI? How does the data persist?
The `KELs` are what establishes the root of trust in `KERI`. So you have a `SCI` and a `KEL`. The `KEL` is ordered with respect to the SCI by the controller. You don't need total ordering with respect to other identifiers to establish the root of trust in `KERI`, because the controller is the one and only, who orders events.\
In blockchains you have total ordering, which you need for double spend protecting in cryptocurrencies, but not in `KERI`.\
For people in blockchain this is a bit hard to grasp, but we don’t need hash chained data structure of events on single identifier nor the *ordering* those, I just need logs, I need *append-only logs of events* to establish the authority.\
And so I defend myself against `duplicity`.\
(_SamMSmith_)

## Why is end-verifiability such a big thing in KERI?
In brief: with end-verifiability anyone can verify anywhere at anytime, without the need to trust anyone or anything in between.

Because any copy of an `end-verifiable` record or log is sufficient, any infrastructure providing a copy is replaceable by any other infrastructure that provides a copy, that is, any infrastructure may do. Therefore the infrastructure used to maintain a log of transfer statements is merely a `secondary root-of-trust` for control establishment over the identifier. This enables the use of ambient infrastructure to provide a copy of the log. The _combination_ of end verifiable logs served by ambient infrastructure _enables_ ambient verifiability, that is, anyone can verify anywhere at anytime. This approach exhibits some of the features of certificate transparency and key transparency with end-verifiable event logs but differs in that each identifier has its own chain of events that are rooted in a self-certifying identifier.

# Q&A section Why the internet is broken

## Why would the internet be broken?
The Internet Protocol (IP) is broken because it has no security layer.\
<img src="../images/internet_broken.png" alt="Internet stack shows omissions" border="0" width="500">
(_SamMSmith_)

## How can the internet be fixed?
Establish authenticity between the key pair and the identifier of IP packet’s message payload. [See more](https://ssimeetup.org/key-event-receipt-infrastructure-keri-secure-identifier-overlay-internet-sam-smith-webinar-58/) in presentation.

<img src="../images/identity_system_security_overlay.png" alt="identity system security overlay" border="0" width="800">
(_SamMSmith_)

## What's wrong with SSL certificate intermediairies?
Administrative Identifier Issuance and Binding; especially the binding between keypair and identifier based on an assertion of an intermediairy administrator. This is what's weak and therefore wrong. [See more](https://ssimeetup.org/key-event-receipt-infrastructure-keri-secure-identifier-overlay-internet-sam-smith-webinar-58/) in presentation.\
_(@henkvancann)_

## What's DNS Hijacking
A DNS hijacking wave is targeting companies at an almost unprecedented scale. Clever trick allows attackers to obtain valid TLS certificate for hijacked domains. [more](https://arstechnica.com/information-technology/2019/01/a-dns-hijacking-wave-is-targeting-companies-at-an-almost-unprecedented-scale/).\
_(@henkvancann)_

## What is 'platform locked trust' and why should we bother?
The `IPv4 layer` was become a standard internet transport layers over the years. It is a very strong structure. The transport layer has no security build into it. So the trust layer has to be something higher in the stack. However in the Support Application layers that sit on top of that IPv4, no standardization has taken place yet. It is a highly segmented layer and trust is therefore *locked* in those segments or platforms; it's not interoperable accross the internet. E.g. platform `Facebook` provides an identity system that only works within their domain. That's the same with for example `Google` or any number of blockchain.\
We don't have a trustable interoperability. And that leads to the idea that the internet is broken. We want to fix that, we don't want a domain segmented internet trust map, a bifurcated internet, we want to have a single trust map. This is the motivation for `KERI`.\
(_SamMSmith_)

## How to repair the internet trust layer?
With a waist and a neck. <img src="../images/platform_locked_trust.png" alt="Platform locked trust" border="0" width="400" style="float:left"><img src="../images/waist_neck.png" alt="Waist and neck" border="0" width="400" style="float:right">
_(@henkvancann)_

## What role does KERI play in the suggested "repair of the internet"?
Much of the operation of internet infrastructure is inherently decentralized, but control over the value transported across this infrastructure may be much less so.\
Centralized value capture systems concentrate value and power and thereby provide both strong temptations for malicious administrators to wield that concentrated power to extract value from participants. \
We believe that _decentralization of value transfer_ is essential to building trust. Consequently a key compo- nent for a decentralized foundation of trust is an interoperable decentralized identity system. [Source: whitepaper page 7](https://github.com/SmithSamuelM/Papers/blob/master/whitepapers/KERI_WP_2.x.web.pdf)

# Q&A section Identifiers

## How is a KERI identifier different than a regular identifier in DID methods?
A self-sovereign identifier that is not self-certifying is dependent of infrastructure and is not fully autonomous and not fully porteable. KERI uses autonomic identifiers, fully cryptographically derivable and portable.
_(@henkvancann)_

## Is my KERI identifier public?
In the direct mode (peer to peer) KERI can be used to keep identifiers private to the peers or group involved. In the indirect mode all identifiers are public. The privacy of the individual, group or object described by the identifier is weak because anyone can bind and indentifier to a subject anytime and anywhere. Fortunately, this binding is weak too, As soon as controllers and verfiers sign statements / events related to an identifier, that's when the binding gets strong and subjects publicly exposed.\
_(@henkvancann)_

## Is a KERI identifier GPDR proof?
KERI enables support for GDPR’s right to be forgotten.\
{TBW prio 1}\
_(@henkvancann)_

## What do I need a self-certifying identifier for?
It is a cryptographically derived, strong binding between a controller, a keypair and an identifier. No weak bindings introduced by administration present.
_(@henkvancann)_

## What do I need a self-addressing identifier for?
{TBW}

## What do I need a multi-sig self-addressing identifier for?
To get even more security in terms of your signing scheme.\
(_SamMSmith_)

## What do I need a delegated self-adressing identifier for?
To be able to horizontally scale your identifier system, that consists of a root identifier that manages a bunch of other delegated identifier. Created with a cryptographically derived strong binding, all the way through your infrastructure. Not dependent on any administration at all. \
(_SamMSmith_)

## What do I need a self-signing identifier for?
Often it is an efficiecy measure where the identifier includes the signature as your `content-addressable hash`.\
_(SamMSmith)_

## What do I need a non-transferable identifier for, as KERI supports transferable identifiers?
Its use is different. Many applications of self-certifying identifiers only require temporary use after which the identifier is abandoned. These are called ephemeral identifiers. Other applications may only attach a limited amount of value to the identifier such that replacing the identifier is not onerous.\
Because a non-transferable (ephemeral) identifier is not recoverable in the event of compromise, the only recourse is to replace the identifier with another identifier. In some applications this may be preferable, given the comparable simplicity of maintaining key state.\
In either of these cases a non-transferable self-certifying identifier is sufficient.

# Q&A section Event logs

## What is a Key Event Log?
It's the basis of the source of truth for KERI identifiers. KERI enables cryptographic proof-of-control-authority (provenance) for each identifier. A proof is in the form of an identifier’s key event receipt log (KERL), after a validator verified the registered events, in the chain of events: the key event log (KEL).\
_(@henkvancann)_

## Why is a Key Event Log crucially important?
Without KELs, we wouldn't have a chain of registered and signed key events for an identifier. The availability and consistency of the KEL is crucial for next steps: verification of events and duplicity checks. Without verified KELs there will be no KERL for identifiers at hand.\
_(@henkvancann)_

## How do I create a KEL?
By a key inception event. A controller creates a key pair and binds this to his/her KERI identifier.
There will be wallet software and an API available in the course of code development and also a DID scheme (DID:UN) that invokes calls to those APIs during resolution of the DID.
_(@henkvancann)_

## How can I trust a KEL?
It is secured by a `Distributed Hash Table`, so internal inconsistencies are cryptographically provable. If they they are internal consistent the first level of trust is established. Furthermore a KERL is end-verifiable to the root-of-trust. You don't need the whole KERL at all times [Read more why](https://github.com/henkvancann/keri/blob/master/docs/Q-and-A.md#do-i-need-to-show-the-full-log-kel-to-anybody-i-transact-with-even-though-id-only-like-to-show-a-part-of-it-for-example-a-virtual-credential). Together with the external consistency (duplicity check)
_(@henkvancann)_

# Q&A section Inconsistency and duplicity

## What kind of Inconsistencies do we have?
An internally inconsistent KEL, this simply won't verify. 
External inconsistency: two versions of the key event log (KEL).

## How can it be garantueed than an identifier represents a certain identity and not another one?
KERI takes advantage of its cryptographic root of trust with strong bindings, to get an inviable guarantee, based on both internal consistency for the cryptographic root of trust and external consistency using ambient duplicity detection.

## What is Duplicity?
See the [definition](#duplicity). What it means is that we have a way to make judgements about trust in entities.\
_(@henkvancann)_

## What does duplicity look like?
Duplicity takes two forms. In the first form, a `controller` may be deemed duplicitous whenever it produces an event message that is inconsistent with another event message it previously produced. In the second form, a witness may be deemed duplicitous when it produces an event _receipt_ that is in- consistent with another event receipt it previously produced.\
_(SamMSmith)_

## Why should we care about Duplicity?
Duplicity becomes a basis for distrust in a controller or its witnesses. _(SamMSmith)_

# Q&A section Key rotation

## What is Key Rotation?
Changing the key, i.e., replacing it by a new key. The places that use the key or keys derived from it (e.g., authorized keys derived from an identity key, legitimate copies of the identity key, or certificates granted for a key) typically need to be correspondingly updated.

the main purpose of key rotation it to either prevent or recover from a successful compromise of one or more private keys by an exploiter.\
[Source](https://csrc.nist.gov/glossary/term/Key_Rotation).

## Why bother about key rotation?
The primary purpose of rotating encryption keys is not to decrease the probability of a key being broken, but to reduce the amount of content encrypted with that key so that the amount of material leaked by a single key compromise is less.

However, for _signing keys_ there is a concrete reason: say it takes X months of computation (expected value given your threat model) to crack a key, and you rotate your signing key every 𝑋−1 months and revoke the old one, then by the time an attacker has cracked the key, any new signatures produced by the attacker will either be A) rejected by clients because of key expiry, or B) back-dated to before the key revocation (which should also raise warning in clients).\
[Source](https://crypto.stackexchange.com/questions/41796/whats-the-purpose-of-key-rotation).

## Why does KERI solve interoperability with its key rotation scheme? 
KERI uses plain old digital signatures from PKI, intentionally, so that it may be truly universally applied. KERI solves that hard problem of PKI, that is, key rotation in a standard way. Without a standard way of addressing key rotation, there is no interoperability between systems, they break when you rotate keys because no one knows how to verify the key rotation was done properly. KERI solves that problem.


## Wat is Pre-rotation?
Pre-rotation is a _cryptographical commitment (a hash)_ to the _next_ private key in the rotation-scheme. (_@henkvancann_)\
The pre-rotation scheme provides secure verifiable rotation that mitigates successful exploit of a given set of signing private keys from a set of (public, private) key-pairs when that exploit happens sometime **after** its creation _and_ its first use to issue a `self-certifying identifier`. In other words, it assumes that the private keys remains private **until after** issuance of the associated identifier.\
[Source: chapter Pre-rotation in whitepaper](https://github.com/SmithSamuelM/Papers/blob/master/whitepapers/KERI_WP_2.x.web.pdf)

## Why hasn't pre-rotation or forward chaining been done before?
I first wrote about in 2018, it's been public knowledge ever since. I guess people just don't read.\
(_SamMSmith_)

# Q&A section KEL and KERL

## What is the difference between KEL and KERL?
The word 'Receipt' explains it all: the sender signs off the verification of the KEL done by the recipient. That _Receipt_ is hosted in the KERL and is the root-of-trust for KERI.\
<img src="../images/Direct-mode-kel-kerl.png" alt="Direct mode: kel and kerl difference charted" border="0" width="600" style="float:left">
The analogy is the difference between a _two-way_ - and a _three-way handshake_: Did I, the recepient, only verify that the sender's message was valid (two-way using KEL, arrow left to right) or did the sender _sign off the receipt_ of that verification by the recipient (three-way in KERL, arrow right to left)
_(@henkvancann)_

# Q&A section Wallets

## Why do I need a wallet for KERI?
Yes. [Universal wallet](https://w3c-ccg.github.io/universal-wallet-interop-spec/) - would do - with a thin layer on top of it. \
A wallet needs to be adapted to KERI to be able to carry KERI identifiers.\
{TBW}\
(_SamMSmith_) / _(CharlesCunningham)_


## How can I backup the KERI identifiers in my wallet?
{TBW}
## Can I receive crypto money in my KERI wallet?
We don't need a crypto currency embedded in the KERI system, we can use any other crypto currency system for payment. So the design of the KERI system has left crypto token control out.\
_(@henkvancann)_

## Does a KERI wallet store virtual credentials connect to my identifiers?
The KERI whitepaper has little about virtual credentials and KERI's place in the W3C SSI space for DIDs and VCs. The reason is that KERI is mainly a level 1 and level 2 solution in the trust-over-ip framework.\
_(@henkvancann)_

In this presenation of Sam, there's a lot about the relation between KERI and VCs: https://github.com/SmithSamuelM/Papers/blob/master/presentations/GLEIF_with_KERI.web.pdf

# Q&A section Signatures

## Who can sign off my proofs and identifiers using KERI?
Depends on what you mean with proof. KERI is content agnostic, so any cryptographic proof can be referenced and signed in a KEL, even a third party signature. As far as KERI-internal proofs are concerned a subject-controller, a delegated controller and combination of (fractioned) multi-signatures can prove authoritative conrol over a key and over a pre-rotated key.
_(@henkvancann)_
{TBW prio 1}

## What is the practical use of signatures?
In general they can proof the control of a private key at a certain point back in time.
_(@henkvancann)_

## Do verifiers, validators, witnesses and watchers all sign off `payloads`?
Yes they do. For every cause there is a different payload. The main reason why all roles sign off cryptographical references is commitment to those sources (the payload in KERI is often a digest of sources) at a certain point in time.\
_(@henkvancann)_

# Q&A section Proofs

## What does KERI proof?
KERI has the ability to proof various thing:
 - Control over an Autonomous identifier (`AID`).
 - Control over a pre-rotated key
 - Commitment to an Event Log
 - Content addressing by a hash
 - Delegation of control over a key
 - {TBW prio 2}

## Does KERI know whether any message in the Event Logs are valid or true?
No, KERI is data-agnostic. KERI does make no statement about the validity of the payload data.
_(@henkvancann)_
## How can we verify that a statement by a controller is valid?
We may verify that the controller of a private key, (the who), made a statement but not the `validity` of the statement itself.\
(_SamMSmith_)
## How can we trust what was said or written?
We may build trust over time in what was said via histories of verifiably attributable (to whom) consistent statements, i.e. `reputation`.\
(_SamMSmith_)

## Do I need to show the full log (KEL) to anybody I transact with, even though I'd only like to show a part of it, for example a virtual credential?
Yes, because they can't verify the root of trust. They have to have access to the full log at some point in time. Once they verfied to the root of trust, once, they don't have to keep a copy of the full log. They have to keep the event they've seen and any event since, that they need to verify as they go.
(_SamMSmith_)

# Q&A section Private Key Management

## How multi-tasking is the key infrastructure?
KERI has univalent, bivalent and multivalent infrastructures.\
<img src="../images/key-infra-valence.png" alt="Key Infrastruction Valence levels" border="0" width="600">
You need Key-pair Generation and Key Event Signing Infrastructure. And KERI doesn't care how you do it.
From bivalent delegation comes into play. But in fact you can have multivalent infrastructures, all with their own security garantuees and its own key management policies.\
It's all one KERI codebase to do all these infrastructures.\
(_SamMSmith_)

## Does your public-private-key format matter in KERI?
No, because the derivation code allows you to use whichever format you want. So anyone that sees an identifier looks at the first byte or two bytes prepended, it's a derived code, and you can tell exactly what type of public-private-key format we have, e.g. ecdsa.

When you rotate keys, you can always rotate to a different format.

## Can I use BIP32 Hierarchical deterministic keys in KERI to rotate?
Yes, you can derive your keys from that scheme. But KERI is agnostic about it, it wouldn't know.

## Not your keys, not your identity?
In KERI we say _identifier_, because **identity** is a loaded term, lots of misunderstanding around it.\
Pre rotated keys are best practise to keep control of your identifiers. \
If you lose unique control of a key right after inception, before rotation, are there no garantuees to be given for KERLs via witnesses / watchers or whatever. Is the only thing you can do about it, is revoke the key in that case?}\
_(@henkvancann)_

## A wallet is there to store my KERI private keys safely, no?
Currently _Universal wallet_ is aimed at to store KERI keys. The vast majority of security breaches or exposures of keys are originated by the behaviour of people: the way they use wallets. Most rarely due to errors in the wallet software.
{TBW prio 1}

## Are compound private keys (Shamir Secret Sharing) and multisignature schemes possible to incept identifiers?
Yes, complex fractional structures are natively possible in KERI. However only for the non-basic forms (for transferable identifiers).\
_(@henkvancann)_
{TBW prio 1}

## How to delegate control over my private keys that control my identifiers?
{TBW prio 3}



# Q&A section Blockchain

## Does KERI use a blockchain?
No, but KERI uses the same cryptographical building blocks as blockchains do. \
_(@henkvancann)_ \
However, KERI may be augmented with distributed consensus ledgers but does not require them. [Source: section conclusion in whitepaper](https://github.com/SmithSamuelM/Papers/blob/master/whitepapers/KERI_WP_2.x.web.pdf)


## What's the difference between KERI and blockchain?
`KERI` is a unordered hash-linked list of signed Key Event logs and blockchain is a timestamped ordered list of hash-linked blocks of signed transactions. What this means:
1. we don't need ordering in `KERI` and that frees us from consensus protocols in blockchains
2. Hash-linking is done on a lower level in `KERI` and preserves consistency and fuels revealance of duplicity.
3. In `KERI` proofs are cryptographically derived from the root of trust, being the autonomous controller, in blockchains the root-of-trust is a transaction on a ledger; that means the Identifier gets locked on the ledger.\
_(@henkvancann)_

## Why not register identities on an open public ledger like bitcoin, ethereum or soverin?
Because for our purposes we don't need to. Consider two distinct identifier to totally ordered, distributed consensus ledger:
1. the access identifier that allows you to access the ledger. This one is ussually a `SCI`. E.g. on bitcoin your bitcoin address is cryptographically derived from the public key from your keypair.
2. the register identifier that allows you to register an identifier on the ledger. The ledger transaction is validated registering of your identifier, not the cryptographic root-of-trust that the access identifier is using.

The identifier is now locked to that ledger. We want identifiers to be portable accross ledgers, so we don't want to use registration as the root-of-trust, we want to be self-certified all the way.
(_SamMSmith_)

## KERI is basically a series of Pay2PublicKeyHash transactions?
_that you send to witnesses, who observe them and attest to the particular line of operations they see?_

In brief: for KERI that is an apples and oranges comparison.

Because total linear ordering is not needed for a given identifier's event sequencing. Only linear order of that identifier's history. The history's from other events do not have to be ordered with respect to each other. So the secure ordering of a given identifier's history is a completely different class of problem than the secure total ordering of comingled history from multiple identifiers. The security demands are less for the former case. So the equivalent security may be obtained in other ways. While the latter as a side effect of total ordering gives local ordering (per identifier) for free. But securing total ordering may be much harder to do. So one has to be careful, because it's no longer an apples to apples comparison. 
(_SamMSmith_)

# Q&A section Agencies

## What does the governance framework of KERI look like?
> Decentralized systems must coordinate across multiple parties, all acting independently in their own self-interest. This means that the rules of engagement and interaction must be spelled out and agreed to ahead of time, with incentives, disincentives, consequences, processes, and procedures made clear.
{TBW prio 3}
DRAFT BY _(@henkvancann)_

KERI is self-administered, self-governed. What aspects of KERI need governance?

Purist permissionless network proponents will argue that a real decentralized network does not need a governance framework since mathematics and cryptography make sure that proper governance is in place.

The Trust over IP stack includes both a governance stack and technology stack.\
KERI governance roles at *Layer 1* can include: 
- Controller, Entropy hardware and software, KEL, KERL
*Layer 2: Provider governance frameworks*
- Governance of capabilities of digital wallets, agents, and agencies. So the need is primarily to establish baseline security, privacy, and data protection requirements, plus interoperability testing and certification programs, for the following roles:
- Hardware Developers: hardware security modules (HSMs)
- Software Developers: duplicity verification and internal consistency checks
- Agency: ambient availability of KELs and KERLs
*Layer 3: Credential governance frameworks*\
KERI is not an outspoken credential issuance and verification framework. Having said that:
- Controller: inception proof, revocation, delegation proof
- Holders: availability
- Verfifier: external inconsistency proofs
Layer 4: Ecosystem governance framework
- KERIs objective  is to be the spanning trust infrastructure of the whole internet
- Portability of the identities and KERI interoperability between platforms is cryptographically secured
- Inconsistencies "reported" by meercats-like alert governance system
 }

## How can KERI offer consistent services and truth?
A. In a pair-wise setting  each party only needs to be consistent with the other party. Witnesses are not used. It doesn't matter if they lie to each other as long as they lie consistently. KERI does not
enable someone to proof the *veracity* of a statement only the *authenticity* of the statement.\
(_SamMSmith_)

B. If 3 parties are involved in a transaction all they need do is query each other for the copy of the `KEL` that each is using for each other to ensure that there is no duplicity.\
(_SamMSmith_)

C. To **guarantee *undetectable* duplicity** requires a successful eclipse attack* on all the parties. `KERI` merely requires that there be sufficient duplicity detection in the ecosystem. \
This would be a set of `watchers` that the validators trust that record any and all copies of key event logs (`KEL`) that they see.  Because these `watchers` can be anyone and anywhere, any controller of a public identifier is at peril should they choose to publish inconsistent copies of their `KEL`. This removes the incentive to be duplicitous.\
'* Any blockchain system is also vulnerable to such an eclipse attack.\
(_SamMSmith_)

# Q&A section Witness
## Witnesses have no skin in the game, it’s a `nothing at stake` situation, no?
The [KERI slide deck](https://github.com/SmithSamuelM/Papers/blob/master/presentations/KERI2_Overview.web.pdf) has a section called the Duplicity Game.  I suggest reading through that first. Or see the [part of the SSI Meetup](https://ssimeetup.org/key-event-receipt-infrastructure-keri-secure-identifier-overlay-internet-sam-smith-webinar-58/) webinar that tackles this.\
(_SamMSmith_)
{TBW prio 2}

## What is the difference between Key Event Receipt Infrastructure (KERI), and distributed hash tables (DHTs)?
{TBW prio 3}

## As long as witnesses keep lying together no one will ever be able to prove them wrong? 
Witnesses do not make any statement about the content of what is being proved. KERI does not
enable someone to proof the *veracity* of a statement only the *authenticity* of the statement. {TBW} \
(_SamMSmith_)

# Q&A section Watchers

## How can we detect duplicity? Suppose controller has power over witnesses.
In a Public setting `duplicity detection` protects the validator from any duplicity on the part of the controller and any resources such as witness that are controlled by the controller.

Since a given controller in a public setting may not know who all a given validator is using for duplicity detection (watchers etc), the controller can't ensure that they will not be detected. And once detected any value that their public identifier had is now imperiled because *any entity with both copies can proof irrefutably to any other entity that the controller is duplicitous (i.e. not trustable)*. \
(_SamMSmith_)

# Q&A Security Guarantees

## What are the security risks of KERI with regard to the identity protocol?
Harm that can be done to the a `controller`: Unavailability, loss of control authority, externally forced duplicity\
Harm that can be done to a `validator`: _Inadvertent acceptance_ of verifiable - but forged or duplicitous events 

Breaking the promise of global consistemcy by a controller is a provable liability. However, global consistency may only matter after members of that community need to interact, not before.\
(_SamMSmith_)

## How secure is the KERI infrastructure?
KERI changes the discussion about security. From a discussion about the security of _infrastructure_ to a discussion about the security of your _key management infrastructure_. Most people when they think security, the think "oh, blockchain!": permissioned or permissionless, how hard is it to get 51% attack, etc.Non of that matters for KERI. KERI is all about "are your private keys private?!" And if _yes_, that drastically slims down the security discussion to brute force attacks to public keys. And because the next public keys are in fact protected by a hash, you have to brute force the hash algorithm, that is post-quantum secure.
So that is a very high level of infrastructural security.

So private key management and protection is the root of your security in KERI.

## Can I rotate keys with Tangem in KERI?
_Suppose I'd trust a Tangem card for generating public private key pairs at will and the NFC communication allowing to interact with a wallet app._

One of the main concerns is that there is a theoretical link (a binding) between the cards and a user, via the card-ID (CID). However the CID is used only for checking the authenticity and integrity of the chip itself. Tangem publishes and anchors a list of CIDs with corresponding public addresses in a public blockchain. When checking authenticity, the verifier looks up the pub CID and corresponding pub address in the published list, and verifies that the chip controls the correct pub address by means of a challenge-response scheme. 
Even though for blockchain or SSI interactions, a completely new wallet with new pub/priv keypair is generated, the pub/priv key of the CID is used when the authenticity of the chip is checked by means of a challenge response scheme. Everything happens in the client app (2021: iOS or Android; and the client code is open source), where there is no communication with Tangem, so Tangem is not able to see any activity conducted by this CID in an authenticity check.
The CID and corresponding key pairs are not used in any other interaction. A new wallet with new pub/private key pair is generated on chip, with these keys being used for any transactions, signing, etc. 

Q: With the chip firmware being proprietary, how can we be sure that the newly generated private keys for new wallets are not still linked somehow to the cards CID?
A: The firmware is audited by Kudelski and can be verified with a published hash. 
TBD: How can it be verified, when and by whom? If the firmware is not open source, then somebody has to draw a hash from it in an authorized situation. However, Tangem cards are EAL6+ and FIDO2 certified.

On the issue of Rotation:
{TBW prio 2}

## DHTs are not an immutable linear chronology oracle, which is the heart of the actual security problem. You claim KERI solves the security problem with DHTs?!
The immutable linear chronology is provided by the key event log (`KEL`) data structure itself. Getting a full copy is all you need. When retrieving a KEL over a network, then as you say a witness can prune some amount of the latest events, but every witness would have to be compromised for that to be undetectable.\
If parties are so concerned, they could establish a large collectivised set of witnesses that sign and distribute all key events presented to this network (this would essentially be a `Proof of Authority`/federated blockchain but would require (configurable)% compromise for undetectable pruning of recent history. Only PoA/federated because the witness sets are designated by the controllers, so you could not just use arbitrary witnesses who join and leave the network at leisure (afaik).

The difference between the chain and the DHT is that not all DHT nodes act as witnesses for all KELs in the system (in the sense that they dont provide receipts for every KEL and arent referenced in the witness sets of every KEL), but they could all (or at least the ones holding the KEL you seek) still provide availability for KELs and thus would have to all be compromised in order to hide a recent-history-pruning, only one has to transmit the new/complete version to prove all the other versions as being old/incomplete.\
_(CharlesCunningham)_

The point of KERI is to encapsulate all the guarantees within `KEL`s nothing else is needed. DHT is just for resolution process to find a place from where I can get it. This place can change as you like I could even get it in p2p interaction from someone else. DHT seems to be the most reasonable way to build solid infrastructure for resolution process but none of the nodes can actually inject or tamper KELs so you don't have to trust them or get any guarantees from them. Since if the node will miss behave it is very easy to detect that.\
_(RobertMitwicki)_

## You are arguing KERI affords greater security than a decentralized linear event system like Bitcoin?
_...you would be fundamentally arguing that you can record a singular, immutable linear event history more securely than Bitcoin, and I see nothing in KERI that would indicate that._

Read the answer to [this](#keri-is-basically-a-series-of-pay2publickeyhash-transactions) first.

If you read Szabo's paper on threshold structures, you get security of the same type when ever you use a threshold structure, be it MFA, Multi-Sig, or Distributed consensus. They all are using a combination of multiple relatively weak attack surfaces that must be simulatenously compromised for a successful attack. So multiplying simulatneous weak surfaces = functional equivalent of a stronger attack surface.  So when you look at KERI you see that the security is primarily due to cryptographic strength and the witnesses are not the primary source of security but merely secure one thing, that is the availability of the KEL for an identifier. Not the KEL itself. The KEL iteself is secured by signatures.\
From a Validator perspective their security is due to duplicity detection. Successful attack against duplicity detection requires an eclipse attack. Ledgers such as bitcoin are also susceptible to eclipse attacks. So in an apples to apples (resistance to eclipse attack) a KERI watcher network of comparable reach (1000's of watchers) would have comparable resistance to an eclipse attack.


# Q&A Virtual Credentials

## Why doesn't KERI use certification as a root of trust?
Why do we want portable identifiers instead of the Ledger Locked IDs, since we have DIDs that can resolve a ledger locked Id uniformly? You say “We don’t want to use certification as a root of trust, we want to do it self-certified all the way” -> what about the issuance of a credential based on the ledger locking, isn’t that beneficial?

## Is Custodianship of KERI identifiers possible? 
_Or does (Delegated, Multi-sig) Self-Adressing do the job?_