# Q&A about KERI
<img src="../images/Keri_logo_color_on_white.png" alt="KERI logo" border="0" width="300">

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
      - [Ambient verifiability](#ambient-verifiability)
      - [Agent](#agent)
      - [Agency](#agency)
      - [Autonomic Identifier](#autonomic-identifier)
      - [Autonomic Namespace](#autonomic-namespace)
      - [Autonomic idenity system](#autonomic-idenity-system)
      - [Content-addressable hash](#content-addressable-hash)
      - [Controller](#controller)
      - [Correlation](#correlation)
      - [Cryptocurrency](#cryptocurrency)
      - [Decentralized Identity](#decentralized-identity)
      - [Derivation code](#derivation-code)
      - [Duplicity](#duplicity)
      - [Entropy](#entropy)
      - [Establishment Event](#establishment-event)
      - [End verifiable log](#end-verifiable-log)
      - [Entity](#entity)
      - [External consistency](#external-consistency)
      - [Inception Event](#inception-event)
      - [Inconsistency](#inconsistency)
      - [Identity](#identity)
      - [Internal inconsistency](#internal-inconsistency)
      - [KERI Agreement Algorithm for Control Establishment](#keri-agreement-algorithm-for-control-establishment)
      - [Key](#key)
      - [Key Event Log](#key-event-log)
      - [Key Event Receipt Log](#key-event-receipt-log)
      - [Non-Establishment Event](#non-establishment-event)
      - [Payload](#payload)
      - [Public Key Infrastructure](#public-key-infrastructure)
      - [Root of trust](#root-of-trust)
      - [Seal](#seal)
      - [Secret](#secret)
      - [Self Addressing Identifier](#self-addressing-identifier)
      - [Self Certifying Identifier](#self-certifying-identifier)
      - [Self Sovereign Identity](#self-sovereign-identity)
      - [Spanning layer](#spanning-layer)
      - [Transfer](#transfer)
      - [Trust-over-IP](#trust-over-ip)
      - [Validator](#validator)
      - [Verifiable Credential](#verifiable-credential)
      - [W3C DID](#w3c-did)
      - [(Digital Identity) Wallet](#-digital-identity--wallet)

      - [Agency](#agency)
      - [Autonomous Identifier](#autonomous-identifier)
      - [Controller](#controller)
      - [Decentralized Identity](#decentralized-identity)
      - [Duplicity](#duplicity)
      - [Establishment Event](#establishment-event)
      - [External consistency](#external-consistency)
      - [Inception Event](#inception-event)
      - [Inconsistency](#inconsistency)
      - [Internal inconsistency](#internal-inconsistency)
      - [Key Event Log](#key-event-log)
      - [Key Event Receipt Log](#key-event-receipt-log)
      - [Non-Establishment Event](#non-establishment-event)
      - [Public Key Infrastructure](#public-key-infrastructure)
      - [Root of trust](#root-of-trust)
      - [Seal](#seal)
      - [Self Addressing Identifier](#self-addressing-identifier)
      - [Self Certifying Identifier](#self-certifying-identifier)
      - [Self Sovereign Identity](#self-sovereign-identity)
      - [Spanning layer](#spanning-layer)
      - [Validator](#validator)
      - [(Digital Identity) Wallet](#-digital-identity--wallet)
- [Q&A section General](#qa-section-general)
  * [What is KERI?](#what-is-keri)
  * [Is KERI a DID?](#is-keri-a-did-)
  * [Why use KERI?](#why-use-keri-)
  * [Who is KERI? Is it a company or a not for profit?](#who-is-keri--is-it-a-company-or-a-not-for-profit-)
  * [In what programming languages is KERI available?](#in-what-programming-languages-is-keri-available-)
  * [How KERI fit in the 10 principles of SSI by Christopher Allen?](#how-keri-fit-in-the-10-principles-of-ssi-by-christopher-allen)
- [Q&A section KERI operational](#qa-section-keri-operational)
  * [Where can I download KERI?](#where-can-i-download-keri)
  * [Where can we find the code and how could a coder get started?](#where-can-we-find-the-code-and-how-could-a-coder-get-started)
  * [What would you see as the main drawback of KERI?](#what-would-you-see-as-the-main-drawback-of-keri)
  * [How can it be one solution, fit for all SSI problems?](#how-can-it-be-one-solution-fit-for-all-ssi-problems)
  * [Where you would need something quite different than KERI?](#where-you-would-need-something-quite-different-than-keri)
- [Q&A section Userinterface](#qa-section-userinterface)
  * [What does KERI look like?](#what-does-keri-look-like)
  * [Is there a KERI course or webinar available?](#is-there-a-keri-course-or-webinar-available)
  * [Could Keri work for edge computers that need self sovereign identity? How to (selectively) share control over the `SCI`/`SAI` with the owners of the device?](#could-keri-work-for-edge-computers-that-need-self-sovereign-identity--how-to--selectively--share-control-over-the--sci---sai--with-the-owners-of-the-device)
- [Q&A section Root of trust](#qa-section-root-of-trust)
  * [What do I need to trust in KERI?](#what-do-i-need-to-trust-in-keri)
  * [KERI does not need a blockchain, but how does it establish the root-of-trust that we need for SSI? How does the data persist?](#keri-does-not-need-a-blockchain--but-how-does-it-establish-the-root-of-trust-that-we-need-for-ssi--how-does-the-data-persist)
- [Q&A section Why the internet is broken](#qa-section-why-the-internet-is-broken)
  * [Why would the internet be broken?](#why-would-the-internet-be-broken)
  * [How can the internet be fixed?](#how-can-the-internet-be-fixed)
  * [What's wrong with SSL certificate intermediairies?](#what-s-wrong-with-ssl-certificate-intermediairies)
  * [What's DNS Hijacking](#what-s-dns-hijacking)
  * [How to repair the internet trust layer?](#how-to-repair-the-internet-trust-layer)
- [Q&A section Identifiers](#qa-section-identifiers)
- [Q&A section Event logs](#qa-section-event-logs)
- [Q&A section Inconsistency and duplicity](#qa-section-inconsistency-and-duplicity)
- [Q&A section Key rotation](#qa-section-key-rotation)
- [Q&A section KEL and KERL](#qa-section-kel-and-kerl)
- [Q&A section Wallets](#qa-section-wallets)
- [Q&A section Signatures](#qa-section-signatures)
- [Q&A section Proofs](#qa-section-proofs)
  * [How can we verify that a statement by a controller is valid](#how-can-we-verify-that-a-statement-by-a-controller-is-valid)
  * [How can we trust what was said or written?](#how-can-we-trust-what-was-said-or-written)
- [Q&A section Private Key Management](#qa-section-private-key-management)
- [Q&A section Blockchain](#qa-section-blockchain)
  * [Does KERI use a blockchain?](#does-keri-use-a-blockchain)
  * [What's the difference between KERI and blockchain?](#what-s-the-difference-between-keri-and-blockchain)
- [Q&A section Agencies](#qa-section-agencies)
  * [How can KERI offer consistent services and truth?](#how-can-keri-offer-consistent-services-and-truth)
- [Q&A section Witness](#qa-section-witness)
  * [Witnesses have no skin in the game, it’s a `nothing at stake` situation, no?](#witnesses-have-no-skin-in-the-game--it-s-a--nothing-at-stake--situation--no)
  * [As long as witnesses keep lying together no one will ever be able to prove them wrong?](#as-long-as-witnesses-keep-lying-together-no-one-will-ever-be-able-to-prove-them-wrong)
- [Q&A section Watchers](#qa-section-watchers)
  * [How can we detect duplicity? Suppose controller has power over witnesses.](#how-can-we-detect-duplicity--suppose-controller-has-power-over-witnesses)


  - [Q&A section General](#q-a-section-general)
  * [What is KERI?](#what-is-keri-)
  * [Why use KERI?](#why-use-keri-)
  * [Is KERI a DID?](#is-keri-a-did-)
  * [How does KERI match the `trust-over-ip` model and in the `W3C DID standardization`?](#how-does-keri-match-the--trust-over-ip--model-and-in-the--w3c-did-standardization--)
  * [Why use KERI?](#why-use-keri--1)
  * [Who is KERI? Is it a company or a not for profit?](#who-is-keri--is-it-a-company-or-a-not-for-profit-)
  * [In what programming languages is KERI available?](#in-what-programming-languages-is-keri-available-)
  * [How KERI fit in [the 10 principles of SSI](https://medium.com/metadium/self-sovereign-identity-principle-6-portability-4a7105dd0381) by Christopher Allen?](#how-keri-fit-in--the-10-principles-of-ssi--https---mediumcom-metadium-self-sovereign-identity-principle-6-portability-4a7105dd0381--by-christopher-allen-)
- [Q&A section KERI operational](#q-a-section-keri-operational)
  * [Where can I download KERI?](#where-can-i-download-keri-)
  * [Where can we find the code and how could a coder get started?](#where-can-we-find-the-code-and-how-could-a-coder-get-started-)
  * [What would you see as the main drawback of KERI?](#what-would-you-see-as-the-main-drawback-of-keri-)
  * [How can it be one solution, fit for all SSI problems?](#how-can-it-be-one-solution--fit-for-all-ssi-problems-)
  * [Where you would need something quite different than KERI?](#where-you-would-need-something-quite-different-than-keri-)
  * [How does KERI scale](#how-does-keri-scale)
  * [How are KERI witnesses and watchers incentived to spread KELs and KERLs and make them available?](#how-are-keri-witnesses-and-watchers-incentived-to-spread-kels-and-kerls-and-make-them-available-)
  * [How to handle multiple formats of KEL and KERL through time. Will they be backwards compatible?](#how-to-handle-multiple-formats-of-kel-and-kerl-through-time-will-they-be-backwards-compatible-)
  * [Could a KEL or KERL be pruned or charded?](#could-a-kel-or-kerl-be-pruned-or-charded-)
  * [How to bootstrap KERI on the internet? Is it like fax machine; the more there are the more effective it is?](#how-to-bootstrap-keri-on-the-internet--is-it-like-fax-machine--the-more-there-are-the-more-effective-it-is-)
  * [Why does KERI demand signing and digesting the full over-the-wire serialization of a message?](#why-does-keri-demand-signing-and-digesting-the-full-over-the-wire-serialization-of-a-message-)
- [Q&A section Userinterface](#q-a-section-userinterface)
  * [What does KERI look like?](#what-does-keri-look-like-)
  * [Is there a KERI course or webinar available?](#is-there-a-keri-course-or-webinar-available-)
  * [Could Keri work for edge computers that need self sovereign identity? How to (selectively) share control over the `SCI`/`SAI` with the owners of the device?](#could-keri-work-for-edge-computers-that-need-self-sovereign-identity--how-to--selectively--share-control-over-the--sci---sai--with-the-owners-of-the-device-)
- [Q&A section Root of trust](#q-a-section-root-of-trust)
  * [What do I need to trust in KERI?](#what-do-i-need-to-trust-in-keri-)
    + [What the difference between a trust basis and a trust domain?](#what-the-difference-between-a-trust-basis-and-a-trust-domain-)
  * [KERI does not need a blockchain, but how does it establish the root-of-trust that we need for SSI? How does the data persist?](#keri-does-not-need-a-blockchain--but-how-does-it-establish-the-root-of-trust-that-we-need-for-ssi--how-does-the-data-persist-)
- [Q&A section Why the internet is broken](#q-a-section-why-the-internet-is-broken)
  * [Why would the internet be broken?](#why-would-the-internet-be-broken-)
  * [How can the internet be fixed?](#how-can-the-internet-be-fixed-)
  * [What's wrong with SSL certificate intermediairies?](#what-s-wrong-with-ssl-certificate-intermediairies-)
  * [What's DNS Hijacking](#what-s-dns-hijacking)
  * [What is 'platform locked trust' and why should we bother?](#what-is--platform-locked-trust--and-why-should-we-bother-)
  * [How to repair the internet trust layer?](#how-to-repair-the-internet-trust-layer-)
  * [What role does KERI play in the suggested "repair of the internet"?](#what-role-does-keri-play-in-the-suggested--repair-of-the-internet--)
- [Q&A section Identifiers](#q-a-section-identifiers)
  * [How is a KERI identifier different than a regular identifier in DID methods?](#how-is-a-keri-identifier-different-than-a-regular-identifier-in-did-methods-)
  * [Is my KERI identifier public?](#is-my-keri-identifier-public-)
  * [Is a KERI identifier GPDR proof?](#is-a-keri-identifier-gpdr-proof-)
  * [What do I need a self-certifying identifier for?](#what-do-i-need-a-self-certifying-identifier-for-)
  * [What do I need a self-addressing identifier for?](#what-do-i-need-a-self-addressing-identifier-for-)
  * [What do I need a multi-sig self-addressing identifier for?](#what-do-i-need-a-multi-sig-self-addressing-identifier-for-)
  * [What do I need a delegated self-adressing identifier for?](#what-do-i-need-a-delegated-self-adressing-identifier-for-)
  * [What do I need a self-signing identifier for?](#what-do-i-need-a-self-signing-identifier-for-)
- [Q&A section Event logs](#q-a-section-event-logs)
  * [What is a Key Event Log?](#what-is-a-key-event-log-)
  * [Why is a Key Event Log crucially important?](#why-is-a-key-event-log-crucially-important-)
  * [How do I create a KEL?](#how-do-i-create-a-kel-)
  * [How can I trust a KEL?](#how-can-i-trust-a-kel-)
- [Q&A section Inconsistency and duplicity](#q-a-section-inconsistency-and-duplicity)
  * [What kind of Inconsistencies do we have?](#what-kind-of-inconsistencies-do-we-have-)
  * [What is Duplicity?](#what-is-duplicity-)
  * [Why should we care about Duplicity?](#why-should-we-care-about-duplicity-)
- [Q&A section Key rotation](#q-a-section-key-rotation)
  * [What is Key Rotation?](#what-is-key-rotation-)
  * [Why bother about key rotation?](#why-bother-about-key-rotation-)
- [Q&A section KEL and KERL](#q-a-section-kel-and-kerl)
  * [What the difference between KEL and KERL?](#what-the-difference-between-kel-and-kerl-)
- [Q&A section Wallets](#q-a-section-wallets)
  * [Why do I need a wallet for KERI?](#why-do-i-need-a-wallet-for-keri-)
  * [How can I backup the KERI identifiers in my wallet?](#how-can-i-backup-the-keri-identifiers-in-my-wallet-)
  * [Can I receive crypto money in my KERI wallet?](#can-i-receive-crypto-money-in-my-keri-wallet-)
  * [Does a KERI wallet store virtual credentials connect to my identifiers?](#does-a-keri-wallet-store-virtual-credentials-connect-to-my-identifiers-)
- [Q&A section Signatures](#q-a-section-signatures)
  * [Who can sign off my proofs and identifiers?](#who-can-sign-off-my-proofs-and-identifiers-)
  * [What is the practical use of signatures?](#what-is-the-practical-use-of-signatures-)
  * [Do verifiers, validators, witnesses and watcher sign off `payloads`?](#do-verifiers--validators--witnesses-and-watcher-sign-off--payloads--)
- [Q&A section Proofs](#q-a-section-proofs)
  * [What does KERI proof?](#what-does-keri-proof-)
  * [Does KERI know whether any message in the Event Logs are valid or true?](#does-keri-know-whether-any-message-in-the-event-logs-are-valid-or-true-)
  * [How can we verify that a statement by a controller is valid?](#how-can-we-verify-that-a-statement-by-a-controller-is-valid-)
  * [How can we trust what was said or written?](#how-can-we-trust-what-was-said-or-written-)
- [Q&A section Private Key Management](#q-a-section-private-key-management)
  * [Not your keys, not your identity?](#not-your-keys--not-your-identity-)
  * [The wallet is there to store my KERI private keys safely, no?](#the-wallet-is-there-to-store-my-keri-private-keys-safely--no-)
  * [Are compound private keys (Shamir Secret Sharing) and multisignature schemes possible to incept identifiers?](#are-compound-private-keys--shamir-secret-sharing--and-multisignature-schemes-possible-to-incept-identifiers-)
  * [How to delegate control over my private keys that control my identifiers?](#how-to-delegate-control-over-my-private-keys-that-control-my-identifiers-)
- [Q&A section Blockchain](#q-a-section-blockchain)
  * [Does KERI use a blockchain?](#does-keri-use-a-blockchain-)
  * [What's the difference between KERI and blockchain?](#what-s-the-difference-between-keri-and-blockchain-)
  * [Why not register identities on an open public ledger like bitcoin, ethereum or soverin?](#why-not-register-identities-on-an-open-public-ledger-like-bitcoin--ethereum-or-soverin-)
- [Q&A section Agencies](#q-a-section-agencies)
  * [How can KERI offer consistent services and truth?](#how-can-keri-offer-consistent-services-and-truth-)
- [Q&A section Witness](#q-a-section-witness)
  * [Witnesses have no skin in the game, it’s a `nothing at stake` situation, no?](#witnesses-have-no-skin-in-the-game--it-s-a--nothing-at-stake--situation--no-)
  * [As long as witnesses keep lying together no one will ever be able to prove them wrong?](#as-long-as-witnesses-keep-lying-together-no-one-will-ever-be-able-to-prove-them-wrong-)
- [Q&A section Watchers](#q-a-section-watchers)
  * [How can we detect duplicity? Suppose controller has power over witnesses.](#how-can-we-detect-duplicity--suppose-controller-has-power-over-witnesses)


<small><i><a href='http://ecotrust-canada.github.io/markdown-toc/'>Table of contents generated with markdown-toc</a></i></small>

## Knowledge you should be confidently applying
- The definitions above
- Public private key pairs
- Bitcoin Improvement Protocols: BIP32, BIP39, BIP44, BIP47, BIP49, BIP84, BIP174
- hierarchical deterministic derivation paths
- Base58
- Eliptic curves
## Actions you should be comfortable with
- Amend knowledge and keep existing knowledge up to date
- create a key pair safely and back it up safely
- recover from a seed
- sweep to a new wallet

# Jump table to categories
- [General](#qa-section-general)
- [KERI operational](#qa-section-keri-operational)
- [Userinterface](#qa-section-userinterface)
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

# Definitions

## Abbreviations
In alphabetic order:\
AID = [Autonomic Identifier](#autonomic-identifier)\
AIS = [Autonomic Identity System](#autonomic-identity-system)\
AN = [Autonomic Namespace](#autonomic-namespace)\
DID = [Decentralized Identity](#decentralized-identity) or Digital Identity dependent of the context.\
DDO = DID Document, look up W3D DID standardization for more info\
DIF = Decentralized Identity Foundation, https://identity.foundation\
DKMI = Decentralized Key Mangement Infrastructure\
IPv4 = standard Internet Protocol, version 4\
KAACE = [KERI Agreement Algorithm for Control Establishment](#keri-agreement-algorithm-for-control-establishment)
KEL = [Key Event Log](#key-event-log)\
KERL = [Key Event Receipt Log](#key-event-receipt-log)\
KERI = [Key Event Receipt Infrastructure](#key-event-receipt-infrastructure)\
PKI = [Public Key Infrastructure]()\
PR = Pull Request; github terminology\
SAI = [Self Addressing Identifier](#self-addressing-identifier)\
SCI = [Self Certifying Identifier](#self-certifying-identifier)\
SSI = [Self Sovereign Identity](#self-sovereign-identity)\
VC = Verifiable Credential, look up W3D DID standardization for more info


Definitions in alphabetic order:

#### Ambient verifiability
Verifiable by anyone, anywhere, at anytime

#### Agent
A representative for an _identity_. MAY require the use of a_wallet_. MAY support _transfer_

#### Agency
Agents can be people, edge computers and the functionality within [`wallets`](#digital-identity-wallet). The service an agent offers is agency.

#### Autonomic Identifier
An identifier that is self-certifying and self-sovereign

#### Autonomic Namespace
A namespace that is self-certifying and hence self-administrating. ANs are therefore portable = truly self sovereign.

#### Autonomic idenity system
In the design of an identity system you need to answer a few questions.

<img src="../images/ais.png" alt="Autonomic Identity System" border="0" width="400">

There's nobody that can intervene with the establishment of the authenticity of a control operation because you can verify all the way back to the root-of-trust.

#### Content-addressable hash
Content addressing is a way to find data in a network using its content rather than its location. The way we do is by taking the content of the content and hashing it. Try uploading an image to IPFS and get the hash using the below button. In the IPFS ecosystem, this hash is called Content Identifier, or CID.
#### Controller
The entity that has the ability to make changes to an _identity_, _cryptocurrency_ or v_erifiable credential_. 

The controller of an `autonomous identifier` is the entity (person, organization, or autonomous software) that has the capability, as defined by derivation, to make changes to an `Event Log`. This capability is typically asserted by the control of a single inception key. In DIDs this is typically asserted by the control of set of cryptographic keys used by software acting on behalf of the controller, though it may also be asserted via other mechanisms. In KERI an AID has one single controller. Note that a DID may have more than one controller, and the DID subject can be the DID controller, or one of them.

#### Correlation
An identifier used to indicate that external parties have observed how wallet contents are related. For example, when a public key is reused, it conveys that some common entity is controlling both identifiers. Tracking correlation allows for software to warn when some new information might be about to be exposed, for example: "Looks like you are about to send crypo currency, from an account you frequently use to a new account you just created."

#### Cryptocurrency
A digital asset designed to work as a medium of exchange wherein individual coin ownership records are stored in a digital ledger or computerized database using strong cryptography to secure transaction record entries, to control the creation of additional digital coin records. See [more](https://en.wikipedia.org/wiki/Cryptocurrency)

#### Decentralized Identity
DID; Decentralized identity is a technology that uses cryptography to allow individuals to create and control their own unique identifiers. They can use these identifiers to obtain `Verifiable Credentials` from trusted organisations and, subsequently, present elements of these credentials as proof of claims about themselves. In this model, the individual takes ownership of their own identity and need not cede control to centralized service providers or companies.

`KERI`s definition of decentralization (centralization) is about _control_ not _spatial distribution_. In our definition _decentralized_ is not necessarily the same as _distributed_. By distributed we mean that activity happens at more than one site. Thus decentralization is about _control_ and distribution is about _place_. To elaborate, when we refer to decentralized infrastructure we mean infrastructure under decentralized (centralized) control no matter its spatial distribution. Thus _decentralized infrastructure_ is infrastructure sourced or controlled by more than one `entity`.


#### Derivation code
{TBW}

#### Duplicity
In `KERI` consistency is is used to described data that is internally consistent and cryptographically verifiably so. Duplicity is used to describe external inconsistency. Publication of two or more versions of a `KEL` log, each of which is internally consistent is duplicity. Given that signatures are non-repudiable any duplicity is detectable and provable given possession of any two mutually inconsistent versions of a `KEL`.  

#### Entropy
Unpredictable information. Often used as a _secret_ or as input to a _key_ generation algorithm.[More](https://en.wikipedia.org/wiki/Entropy_(information_theory))

#### Establishment Event

#### End verifiable log
End verifiable logs on ambient infrastructure enables `ambient verifiability` (verifiable by anyone, anywhere, at anytime). We don't need the intermediate states of the log.

#### Entity
Entities are not limited to natural persons but may include groups, organizations, software agents, things, and even data items. 

#### External consistency
Two or more logs are _externally consistent_ if they are both verfiable internally consistent, to begin with, and the reported copies of the logs that are the same. 

External logs that are _inconsitent_, have at least two reported copies of the logs that are different. That means I have a duplicitous log. We need duplicity detection to be able to garantuee _external consistency_ or put in an different way: duplicity detection protects against external inconsistency.

#### Inception Event

#### Inconsistency

#### Identity
A unique entity. Typically represented with a unique identifier.

#### Internal inconsistency
In KERI we are protected against Internal inconsistency by the hash chain datastructure of the `KEL`, because the only authority that can sign the log is the controller itself. 

#### KERI Agreement Algorithm for Control Establishment
{TBW}

#### Key
A mechanism for granting or restricing access to something. MAY be used to issue and prove, MAY be used to transfer and control over _identity_ and _cryptocurrency_. [More](https://en.wikipedia.org/wiki/Key_(cryptography))

#### Key Event Log

#### Key Event Receipt Log

#### Non-Establishment Event

#### Payload
The term 'payload' is used to distinguish between the 'interesting' information in a chunk of data or similar, and the overhead to support it. It is borrowed from transportation, where it refers to the part of the load that 'pays': for example, a tanker truck may carry 20 tons of oil, but the fully loaded vehicle weighs much more than that - there's the vehicle itself, the driver, fuel, the tank, etc. It costs money to move all these, but the customer only cares about (and pays for) the oil, hence, 'pay-load'. [source](https://softwareengineering.stackexchange.com/questions/158603/what-does-the-term-payload-mean-in-programming).

Now payload in `KERI`. The payload of an item in an `Event Log` is one the following cryptographical building blocks in KERI:
- a content digest hash 
- a root hash of a Merkletree
- a public key
Note that the KERI never puts raw data or privacy sensitive data in a `KEL` or `KERL`.

#### Public Key Infrastructure
A public key infrastructure (PKI) is a set of roles, policies, hardware, software and procedures needed to create, manage, distribute, use, store and revoke digital certificates and manage public-key encryption. [Wikipedia].(https://en.wikipedia.org/wiki/Public_key_infrastructure)

#### Root of trust
Replace human basis-of-trust with cryptographic root-of-trust. With verifiable digital signatures from asymmetric key cryptography we may not trust in “what” was said, but we may trust in “who” said it.\
The root-of-trust is consistent attribution via verifiable integral non-repudiable statements.

#### Seal
A seal is a cryptographic anchor that provides evidence of authenticity; we have:
1. Digist Event Seal
2. Hash tree root Seal
3. Event Seal
Seals deliver authenticity proofs in KERI.

#### Secret
Information controlled by an identity. MAY be used to derive _key_s.

#### Self Addressing Identifier
`SAI`, This is a self certfifying identifier (`SCI`) that has been attached to a certain context or infrastructure at the time of its inception. The inception configuration together with public key and it's `derivation`, forms a digest (hash) plus it's own `derivation code` that constitutes the Prefix of a self-addressing ID.

<img src="../images/sai_sci.png" alt="Self Adressing, self certifying Identifier" border="0" width="800">

#### Self Certifying Identifier
A controller of issues an own Identifier by binding a generated public private keypair to an identifier. After this a controller is able to sign the identifier and create a certificate.

<img src="../images/sci_issue_bind.png" alt="Self Certifying Identifier issuance and binding" border="0" width="400">

The root-of-trust is fully cryptographic, there is no infrastructure associated with it. If we start there we can build a secure system on top of that. It means SCI gives us strong bindings between the keypair, the controller and the identifier. And so it fixes the main weakness of any administratively issued identifier asserting the binding between the keypair and the identifier and between the controller and the identifier, replacing them with all cryptographically strong bindings.

#### Self Sovereign Identity

#### Spanning layer
An all encompassing layer horizontal layer in a software architecture. Each trust layer only spans platform specific applications. It bifurcates the internet trust map. There is no spanning trust layer.
<img src="../images/spanning_layer.png" alt="spanning layer" border="0" width="800">

#### Transfer
The process of changing the _controller_ of _cryptocurrency_, _identity_ or _verifiable credential_. MAY require the use of a _key_.

#### Trust-over-IP
It's a term related to the effort of a foundation. The Trust over IP Foundation is an independent project hosted at Linux Foundation to enable the trustworthy exchange and verification of data between any two parties on the Internet. [More](https://trustoverip.org/about/faq/).

#### Validator
During validation, a `verifier` checks to see if a `verifiable credential` (VC) has been signed by the controller of this VC using the applicable verification method.

#### Verifiable Credential
VC; A data model for conveying claims made by an issuer about a subject. See [vc-data-model](https://www.w3.org/TR/vc-data-model/) for more.

#### W3C DID
The W3C consortium Decentralized ID standardization. [More](https://w3c.github.io/did-core/).

#### (Digital Identity) Wallet
In our context it is software and sometimes hardware that serves as a key store and functionality. Keys can be private keys and public keys, hashes and pointers. Functionality can be signing, invoices (receive), send, virtual credentials, delegation, etc. This is the [`agency`](#agency) part of a wallet. \
[More about digital ID Wallets](https://www.thalesgroup.com/en/markets/digital-identity-and-security/government/identity/digital-identity-services/digital-id-wallet)\
[More about cryto Wallets](https://cryptocurrencyfacts.com/what-is-a-cryptocurrency-wallet/).

# Q&A section General

## What is KERI?
Key Event Receipt Infrastructure; a secure identifier overlay for the internet.
## Why use KERI?
Because there is no secure universal trust layer for the internet, currently (2020).\
KEI is both privacy preserving and context-independent extensible. That means KERI is interoperable accross areas of application on the internet. It does so securely, with minimal sufficient means. 
_(@henkvancann)_

## Is KERI a DID?
`KERI` is not a `DID` method. The related `DID` method is [`did:un`](https://github.com/decentralized-identity/keri/blob/master/did_methods/un.md). A session at the recent **IIW31** presented by Jolocom’s *Charles Chunningham* examines overlap between data models of DID documents and `KERI` identifiers [here](https://jolocom.io/blog/as-seen-at-iiw31-keri/).\
_(@henkvancann)_

## How does KERI match the `trust-over-ip` model and in the `W3C DID standardization`?
[Trust-over-IP](#trust-over-ip):
- Its goal is to be the missing authentication layer of the internet. That's a pretty well matching objective.
- Layer 1 (settlement layer): Where other `DID`s use blockchains or databases to register identities and settle 'transactions' between between, `DDO`s, and `VC`s, KERI uses homegrown native structures: `KEL` and `KERL`.
_(@henkvancann)_
- Layer 2 (communication layer): Non existing in KERI, because KERI is end-verifiable. KERI can use any other means of communication between actors in the ecosystem
- Layer 3 (transaction layer): Since KERI focuses on the more fundamental part of authentication for the internet, you won't find match functionality for usual trust-over-IP transaction like VCs or money.
- Layer 4 (application layer): {TBW}
_(@henkvancann)_

[W3C DID]():
1. The KERI developers provisionally design DID:UN, which might become a mixture of DID:KEY, DID:PEER, and DID:WEB, combinable with more functional DIDs in the Identity spectrum DID:SOV, DID:ETHR, etc.
2. No verifiable credentials
_(@henkvancann)_

## Why use KERI?
Because there is no secure universal trust layer for the internet, currently (2020).

## Who is KERI? Is it a company or a not for profit?
KERI sits under the *Decentralized Identity Foundation*, [DIF](https://identity.foundation), and within that in the *Identity and Discovery* Workgroup.
Due to its licensing structure, KERI isn't owned by anyone and everyone at the same time. The Intellectual Property Right of KERI is hosted with DIF. It is an open source project.

On github KERI is - and will become even more - a thickening bunch of repositories:
 1. https://github.com/decentralized-identity/keri 
 2. https://github.com/decentralized-identity/keripy
 3. etc.
 Lastly, the important man, who founded KERI is *Samuel M. Smith Ph.D.*, operationing from his firm [prosapien.com](https://www.prosapien.com).
 _(@henkvancann)_

## In what programming languages is KERI available?
In Python. It will be available in the coming year in Rust, Javascript and Go (2020).
_(@henkvancann)_

## How KERI fit in [the 10 principles of SSI](https://medium.com/metadium/self-sovereign-identity-principle-6-portability-4a7105dd0381) by Christopher Allen?
KERI is not primarily about self-sovereign identity. KERI is primarily about autonomic identifiers, AIDs. That is identifiers that are self managing. KERI provides proof of control authority over the identifier. What one does with the identifier is not constrained by KERI. But because the primary root of trust of an AID is a KEL which can be hosted by any infrastructure, any identity system (SSI or otherwise) built on top of KERI may also be portable.

So in my opnion portability of the associated identifiers is essential to any truly self-sovereign identity system. That portability, as such, is not one of the principles is a defect in the principles.\
(_SamMSmith_)

Christopher Allen is talking about *portability of information* related to the identity, not the *portability of the identifier itself* with respect to its supporting infrastructure (aka spanning layer).  Indeed, most `DID` methods, including those  that publicly claim to be `SSI` in accordance with the principles do not have portable identifiers. They are locked to a given ledger.\
(_SamMSmith_)

# Q&A section KERI operational

## Where can I download KERI?
On (sub)page(s of) [github](https://github.com/decentralized-identity/keri)

## Where can we find the code and how could a coder get started?
The homepage on github [README.md](../README.md) pretty much sums up all the possibilities to download the available code and how developers can engage in the development process currently. We welcome all help we can get.

## What would you see as the main drawback of KERI?
Its main drawback is that it's nascent.

## How can it be one solution, fit for all SSI problems? 
KERI uses plain old digital signatures from `PKI`, intentionally, so that it may be truly universally applied. KERI solves that hard problem of PKI, that is, key rotation in a standard way. Without a standard way of addressing key rotation, there is no interoperability between systems, they break when you rotate keys because no one knows how to verify the key rotation was done properly. `KERI` solves that problem.\
(_SamMSmith_)

## Where you would need something quite different than KERI?
`KERI` does one thing, it establishes control authority using verifiable portable proofs that are `KEL`s.\
(_SamMSmith_)

## How does KERI scale
`KEL`, `KERL` and `KAACE` might well be very lean alternatives to blockchain based solutions. The hard part is the ambient verifiable architecture.

## How are KERI witnesses and watchers incentived to spread KELs and KERLs and make them available?

## How to handle multiple formats of KEL and KERL through time. Will they be backwards compatible?

## Could a KEL or KERL be pruned or charded?

## How to bootstrap KERI on the internet? Is it like fax machine; the more there are the more effective it is?

## Why does KERI demand signing and digesting the full over-the-wire serialization of a message?
The discussion of `KERI`s approach to *serializing messages and signing and digesting the full over-the-wire serialization* is inconvenient for implementers. The motivation for this approach I am calling Zero Message Malleability as a property of `KERI`. 
This is a "best practices" security first approach that prevents semantic leakage over time that becomes a transaction malleability vulnerability. Indeed `KERI` approach trades off some inconvenience in serialization for better security and reduces the inconvenience of needed to have tightly specified semantics to prevent transaction malleability.\
(_SamMSmith_)

# Q&A section Userinterface
## What does KERI look like?
Currently `KERI` is just code, that can be tested and executed in a terminal on the command line. Private key management of KERI will look like `wallets`.\
Key Event Logs (`KEL`) and Key Event Receipt Log (`KERL`) are files with lots of encrypted stuff in there.\
_(@henkvancann)_

## Is there a KERI course or webinar available?
The [SSI Meetup](https://ssimeetup.org/key-event-receipt-infrastructure-keri-secure-identifier-overlay-internet-sam-smith-webinar-58/) webinar on KERI took place in May 2020 and is a good lesson and source of information.\
_(@henkvancann)_

## Could Keri work for edge computers that need self sovereign identity? How to (selectively) share control over the `SCI`/`SAI` with the owners of the device?
Delegation could be used. There is an [issue about IoT](https://github.com/decentralized-identity/keri/issues/54) key and identifier management with `KERI` that answers this question profoundly.\
(_SamMSmith_)

# Q&A section Root of trust
## What do I need to trust in KERI?
Primary root of trust is KEL not secondary (starts with self cert ID but then after first rotation if any must have KEL.\
(_SamMSmith_)

### What the difference between a trust basis and a trust domain?
A trust basis binds controllers, identifiers, and key-pairs.

A trust domain is the ecosystem of interactions that rely on a trust basis.\


## KERI does not need a blockchain, but how does it establish the root-of-trust that we need for SSI? How does the data persist?
The `KELs` are what establishes the root of trust in `KERI`. So you have a `SCI` and a `KEL`. The `KEL` is ordered with respect to the SCI by the controller. You don't need total ordering with respect to other identifiers to establish the root of trust in `KERI`, because the controller is the one and only, who order events.\
In blockchains you need total ordering, which you need for double spend protecting in cryptocurrencies, but not in `KERI`.\
For people in blockchain this is a bit hard to grasp, but we don’t need hash chain data structure of events on single identifier nor the *ordering* those, I just need logs, I need *append-only logs of events* to establish the authority.\
And so I defend myself against `duplicity`.\
(_SamMSmith_)

# Q&A section Why the internet is broken

## Why would the internet be broken?
The Internet Protocol (IP) is bro-ken because it has no security layer.\
<img src="../images/internet_broken.png" alt="Internet stack shows omissions" border="0" width="600">
(_SamMSmith_)

## How can the internet be fixed?
Establish authenticity between the key pair and the identifier of IP packet’s message payload. [See more](){TBW} in presentation.

<img src="../images/identity_system_security_overlay.png" alt="identity system security overlay" border="0" width="800">
(_SamMSmith_)

## What's wrong with SSL certificate intermediairies?
Administrative Identifier Issuance and Binding; especially the binding between keypair and identifier based on an assertion of an intermediairy administrator. This is what's weak and therefore wrong. [See more]() {TBW} in presentation.\
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

## Is a KERI identifier GPDR proof?

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
(_SamMSmith_)

# Q&A section Event logs

## What is a Key Event Log?

## Why is a Key Event Log crucially important?

## How do I create a KEL?

## How can I trust a KEL?

# Q&A section Inconsistency and duplicity

## What kind of Inconsistencies do we have?

## What is Duplicity?

## Why should we care about Duplicity?

# Q&A section Key rotation

## What is Key Rotation?

## Why bother about key rotation?

# Q&A section KEL and KERL

## What the difference between KEL and KERL?

# Q&A section Wallets

## Why do I need a wallet for KERI?

## How can I backup the KERI identifiers in my wallet?

## Can I receive crypto money in my KERI wallet?
We don't need a crypto currency embedded in the KERI system, we can use any other crypto currency system for payment. So the design of the KERI system has left crypto token control out.\
_(@henkvancann)_
## Does a KERI wallet store virtual credentials connect to my identifiers?

# Q&A section Signatures

## Who can sign off my proofs and identifiers?

## What is the practical use of signatures?

## Do verifiers, validators, witnesses and watcher sign off `payloads`?

# Q&A section Proofs

## What does KERI proof?

## Does KERI know whether any message in the Event Logs are valid or true?

## How can we verify that a statement by a controller is valid?
We may verify that the controller of a private key, (the who), made a statement but not the `validity` of the statement itself.\
(_SamMSmith_)
## How can we trust what was said or written?
We may build trust over time in what was said via histories of verifiably attributable (to whom) consistent statements, i.e. `reputation`.\
(_SamMSmith_)

# Q&A section Private Key Management

## Not your keys, not your identity?

## The wallet is there to store my KERI private keys safely, no?

## Are compound private keys (Shamir Secret Sharing) and multisignature schemes possible to incept identifiers?

## How to delegate control over my private keys that control my identifiers?

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

# Q&A section Agencies

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

{TBW}
## As long as witnesses keep lying together no one will ever be able to prove them wrong? 
Witnesses do not make any statement about the content of what is being proved. KERI does not
enable someone to proof the *veracity* of a statement only the *authenticity* of the statement. {TBW} \
(_SamMSmith_)
# Q&A section Watchers

## How can we detect duplicity? Suppose controller has power over witnesses.
In a Public setting `duplicity detection` protects the validator from any duplicity on the part of the controller and any resources such as witness that are controlled by the controller.

Since a given controller in a public setting may not know who all a given validator is using for duplicity detection (watchers etc), the controller can't ensure that they will not be detected. And once detected any value that their public identifier had is now imperiled because *any entity with both copies can proof irrefutably to any other entity that the controller is duplicitous (i.e. not trustable)*. \
(_SamMSmith_)