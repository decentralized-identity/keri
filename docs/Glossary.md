# Definitions

## Abbreviations
In alphabetic order:\
ACDC = Authentic Chained Data Container Task Force
AID = [Autonomic Identifier](#autonomic-identifier)\
AIS = [Autonomic Identity System](#autonomic-identity-system)\
AN = [Autonomic Namespace](#autonomic-namespace)\
DEL = [Duplicitous Event Log](#duplicitous-event-log)\
DID = [Decentralized Identity](#decentralized-identity) or Digital Identity dependent of the context.\
DIF = Decentralized Identity Foundation\
DDO = DID Document, look up W3D DID standardization for more info\
DHT = Distributed Hash Table\
DIF = Decentralized Identity Foundation, https://identity.foundation\
DKMI = Decentralized Key Mangement Infrastructure\
HSM = Hardware Security Module\
IPv4 = standard Internet Protocol, version 4\
KAACE = [KERI Agreement Algorithm for Control Establishment](#keri-agreement-algorithm-for-control-establishment)
KEL = [Key Event Log](#key-event-log)\
KERL = [Key Event Receipt Log](#key-event-receipt-log)\
KERI = [Key Event Receipt Infrastructure](#key-event-receipt-infrastructure)\
KID = [KERI Implementation/Improvement Docs](#keri-implementation-Improvement-docs)
LOA = [Levels Of Assurance](#levels-of-assurance)\
PKI = [Public Key Infrastructure](#public-key-infrastructure)\
PoA = Proof of Authority\
PR = Pull Request; github terminology\
SAI = [Self Addressing Identifier](#self-addressing-identifier)\
SASCI = [Self Addressing self certifying Identifier](#self-addressing-identifier)\
SCI = [Self Certifying Identifier](#self-certifying-identifier)\
SSI = [Self Sovereign Identity](#self-sovereign-identity)\
TEL = [Transaction Event Log](#transaction-event-log)
VC = Verifiable Credential, look up W3D DID standardization for more info\
VDS = [Verifiable Data Structure](#verifiable-data-structure)
WASM = [WebAssembly](#WebAssembly)


Definitions in alphabetic order:

#### Authentic Chained Data Container Task Force
The purpose of the Authentic Chained Data Container (ACDC) Task Force  is to draft a TSS (ToIP Standard Specification) that defines the standard requirements for the semantics of Authentic Provenance Chaining of Authentic Data Containers. [See more](https://wiki.trustoverip.org/display/HOME/ACDC+%28Authentic+Chained+Data+Container%29+Task+Force)

#### Ambient verifiability
Verifiable by anyone, anywhere, at anytime. E.g. Ambient Duplicity Detection describes the possibility of detecting duplicity by anyone, anywhere, anytime.

#### Agent
A representative for an _identity_. MAY require the use of a_wallet_. MAY support _transfer_

#### Agency
Agents can be people, edge computers and the functionality within [`wallets`](#digital-identity-wallet). The service an agent offers is agency.

#### Autonomic Identifier
An identifier that is self-certifying and self-sovereign

#### Autonomic Namespace
A namespace that is self-certifying and hence self-administrating. ANs are therefore portable = truly self sovereign.\
See basic explanation of [Namespace](#namespace).

#### Autonomic idenity system
In the design of an identity system you need to answer a few questions.

<img src="../images/ais.png" alt="Autonomic Identity System" border="0" width="400">

There's nobody that can intervene with the establishment of the authenticity of a control operation because you can verify all the way back to the root-of-trust.

#### Claim
An assertion of the truth of something, typically one which is disputed or in doubt. A set of claims might convey personally identifying information: ½name, address, date of birth and citizenship, for example. ([Source](https://www.identityblog.com/?p=352)).

#### Content-addressable hash
Content addressing is a way to find data in a network using its content rather than its location. The way we do is by taking the content of the content and hashing it. Try uploading an image to IPFS and get the hash using the below button. In the IPFS ecosystem, this hash is called Content Identifier, or CID.
#### Controller
The entity that has the ability to make changes to an _identity_, _cryptocurrency_ or _verifiable credential_. 

The controller of an `autonomous identifier` is the entity (person, organization, or autonomous software) that has the capability, as defined by derivation, to make changes to an `Event Log`. This capability is typically asserted by the control of a single inception key. In DIDs this is typically asserted by the control of set of cryptographic keys used by software acting on behalf of the controller, though it may also be asserted via other mechanisms. In KERI an AID has one single controller. Note that a DID may have more than one controller, and the DID `subject` can be the DID controller, or one of them.

#### Correlation
An identifier used to indicate that external parties have observed how wallet contents are related. For example, when a public key is reused, it conveys that some common entity is controlling both identifiers. Tracking correlation allows for software to warn when some new information might be about to be exposed, for example: "Looks like you are about to send crypo currency, from an account you frequently use to a new account you just created."

#### Cryptocurrency
A digital asset designed to work as a medium of exchange wherein individual coin ownership records are stored in a digital ledger or computerized database using strong cryptography to secure transaction record entries, to control the creation of additional digital coin records. See [more](https://en.wikipedia.org/wiki/Cryptocurrency)

#### Decentralized Identity
DID; Decentralized identity is a technology that uses cryptography to allow individuals to create and control their own unique identifiers. They can use these identifiers to obtain `Verifiable Credentials` from trusted organisations and, subsequently, present elements of these credentials as proof of claims about themselves. In this model, the individual takes ownership of their own identity and need not cede control to centralized service providers or companies.

`KERI`s definition of decentralization (centralization) is about _control_ not _spatial distribution_. In our definition _decentralized_ is not necessarily the same as _distributed_. By distributed we mean that activity happens at more than one site. Thus decentralization is about _control_ and distribution is about _place_. To elaborate, when we refer to decentralized infrastructure we mean infrastructure under decentralized (centralized) control no matter its spatial distribution. Thus _decentralized infrastructure_ is infrastructure sourced or controlled by more than one `entity`.

#### Duplicitous event log
Or DEL. This is a record of _inconsistent_ event messages produced by a given controller or witness with respect to a given `KERL`. The duplicitous events are indexed to the corresponding event in a KERL. A duplicitous event is represented by a set of two or more provably mutually inconsistent event messages with respect to a KERL. Each `juror` keeps a duplicitous event log (DEL) for each controller and all designated witness with respect to a KERL. Any validator may confirm duplicity by examining a DEL.

#### Derivation code
To properly extract and use the `public key` embedded in a self-certifying identifier we need to know the cryptographic _signing scheme_ used by the key pair. KERI includes this very compactly in the identifier, by replacing the pad character (a character used to fill a void to able to always end up with a fixed length public key) with a special character that encodes the derivation process. Call this the derivation code.
```
For example suppose that the 44 character Base-64 with trailing pad charac- ter for the public key is as follows:
_F5pxRJP6THrUtlDdhh07hJEDKrJxkcR9m5u1xs33bhp=_
If B is the value of the derivation code then the resultant self-contained string is as follows:
_BF5pxRJP6THrUtlDdhh07hJEDKrJxkcR9m5u1xs33bhp_
```
All crypto material appears in `KERI` in a fully qualified representation that includes a derivation code prepended to the crypto-material.
<img src="../images/derivation-code.png" alt="Derivation Code" border="0" width="600">

#### Duplicity
In `KERI` consistency is is used to described data that is internally consistent and cryptographically verifiably so. Duplicity is used to describe **external inconsistency**. Publication of two or more versions of a `KEL` log, each of which is internally consistent is duplicity. Given that signatures are non-repudiable any duplicity is detectable and provable given possession of any two mutually inconsistent versions of a `KEL`.  

In common language 'duplicity' has a slightly different connotation: 'two-facedness', 'dishonesty', 'deceitfulness', 'deviousness,'two-facedness', 'falseness'.
#### End verifiable
If a log is end verifiable, this means that the log may be verified by any end user that receives a copy. No trust in intervening infrastructure is needed to verify the log and validate the content. 

#### Entropy
Unpredictable information. Often used as a _secret_ or as input to a _key_ generation algorithm.[More](https://en.wikipedia.org/wiki/Entropy_(information_theory))

The term entropy is also used to describe the degree of unpredictability of a message. Entropy is then measured in bits. The degree or strength of randomness determines how difficult it would be for someone else to reproduce the same large random number. This is called _collision resistance_. 

#### Establishment Event
An event that establishes control authority. What are the authoritative key-pairs in any point in time. For a trivial system this is one authoritative keypair and it never changes. However, if we need persistance in our identifier and we want to be able to for example overcome compromise of our keys, we need to be able to do something like rotate keys.

#### End verifiable log
End verifiable logs on ambient infrastructure enables `ambient verifiability` (verifiable by anyone, anywhere, at anytime). We don't need the intermediate states of the log.

#### Entity
Entities are not limited to natural persons but may include groups, organizations, software agents, things, and even data items. 

#### Event sourced architecture
It is an Event driven architecture. However in Event Driven you can't ever replay an event.\
In the Event Sourced architecture you recreate states in an asynchronous way. That has in general great scaleability and resiliance characteristics. However, in KERI the driver for event sourcing is security.

#### External consistency
Two or more logs are _externally consistent_ if they are both verfiable internally consistent, to begin with, and the reported copies of the logs that are the same. 

External logs that are _inconsitent_, have at least two reported copies of the logs that are different. That means I have a duplicitous log. We need duplicity detection to be able to garantuee _external consistency_ or put in an different way: duplicity detection protects against external inconsistency.

#### First seen
"First seen" in KERI is the first **verified** event, accepted in the `KEL`. It has no effect on the timing of what has arrived in escrow for example; in escrow there can be garbage.
Every 'first seen' event is propagated world wide within micro-seconds to the watchers. Only in this microseconds windows that you could have a live key conprise attack. If that happens, this where you have to look after this duplicity-attack a bit more in depth to handle it safely. E.g. a valid key rotation.

#### Inception Event
Is a type of Establishment Event, it's the first event that establishes an identifier. \
(_SamMSmith_)

#### Inception Statement
<img src="../images/inception-statement.png" alt="inception statement" border="0" width="200" style="float:right">

**In brief: It's the signed version of a statement containing the inception event with some extra data.**\
(_@henkvancann_)

The inception data must include the public key, the identifier derivation from that public key, and may include other configuration data. The identifier derivation may be simply represented by the `derivation code`. A statement that includes the inception data with attached signature made with the private key comprises a cryptographic commitment to the derivation and configuration of the identifier that may be cryptographically verified by any entity that receives it. \
A KERI inception statement is completely self-contained. No additional infrastructure is needed or more importantly must be trusted in order to verify the derivation and initial configuration (inception) of the identifier. The initial trust basis for the identifier is simply the signed inception statement.\
(_SamMSmith_)
#### Inconsistency
If a reason, idea, opinion, etc. is inconsistent, different parts of it do not agree, or it does not agree with something else. Data inconsistency occurs when similar data is kept in different formats in more than onFBTe file. When this happens, it is important to match the data between files. 

#### Identity
A unique entity. Typically represented with a unique identifier.

#### Internal inconsistency
In KERI we are protected against Internal inconsistency by the hash chain datastructure of the `KEL`, because the only authority that can sign the log is the controller itself. 

#### Javascript Object Signing and Encryption
Or JOSE. JOSE is a framework intended to provide a method to securely transfer claims (such as authorization information) between parties. The JOSE framework provides a collection of specifications to serve this purpose. Related: `JWK`, `JWT`. [More info](https://jose.readthedocs.io/en/latest/)

#### KERI Agreement Algorithm for Control Establishment
{TBW}

#### Keridemlia
It is a contraction of KERI and [Kademlia](https://en.wikipedia.org/wiki/Kademlia). It's the distributed database of Witness IP-addresses based on a Distributed Hash Tabel. It also does the CNAME - stuff that DNS offers for KERI: the mapping between an identifier and it's controller AID stored in the KEL to its current wittness AID and the wittness AID to the IP address.\
(_@henkvancann_)

#### Key
A mechanism for granting or restricing access to something. MAY be used to issue and prove, MAY be used to transfer and control over _identity_ and _cryptocurrency_. [More](https://en.wikipedia.org/wiki/Key_(cryptography))

#### Key Event
A data structure that consist of a header (Key Event header), a configuration section (Key Event Data spans Header and configuration) and signatures (Key event Message spans Data and signatures)\
(_@henkvancann_)

<img src="../images/Key-Event.png" alt="Key Event (message)" border="0" width="400">

#### Key Event Log
Hash-chained Key Events, these are blockchains in a narrow definition, but not in the sense of ordering (not ordered) or global consensus mechanisms (not needed).
_(SamMSmith)_ \
A KEL is KERI's `VDS`: the proof of key state of its identifier.

#### Key Event Receipt Log
Signed Key Events, keeping track of establishment events. To begin with the inception event and any number of rotation events. We call that the _establishment subsequence_. \
(_@henkvancann_)

<img src="../images/inception-rotation.png" alt="inception and any number of rotation events" border="0" width="200" style="float:left">

_(SamMSmith)_

#### Key Event State
Includes the mapping CNAME like, it also contain the witness data\
The KES is never signed by the controller of the AID\
{TBW}

#### KERI Implementation/Improvement Docs
Or KIDs. These docs are modular so teams of contributors can independently work and create PRs of individual KIDs; KIDs answer the question "how we do it". We add commentary to the indivudual KIDs that elaborate on the _why_. It has been split from the _how_ to not bother implementors with the _why_.

#### Level of Assurance
LOA; Identity and other trust decisions are often not binary. They are judgement calls. Any time that judgement is not a simple “Yes/No” answer, you have the option for levels of assurance.
KERI has the same LOAs for entropy and trust in human behaviour preservering the security of keypairs and preservering their own privacy. It has high LOAs for the cryptographical bindings of controllers and identifiers. Also the validation of witnesses and watchtowers has high a LOA.

####  MultiCodec 
Is a self-describing multiformat, it wraps other formats with a tiny bit of self-description. A multicodec identifier is both a varint and the code identifying data. See more at [GitHub Multicodec](https://github.com/multiformats/multicodec)
Multicodec is an agreed-upon codec table. It is designed for use in binary representations, such as keys or identifiers (i.e CID). It is then used as a prefix to identify the data that follows.

#### Namespace 
In an identity system, an identifier can be generalized to a namespace to provide a systematic way of organizing identifiers for related resources and their attributes. A namespace is a grouping of symbols or identifiers for a set of related objects. A namespace employs some scheme for assigning identifiers to the elements of the namespace. A simple name-spacing scheme uses a prefix or prefixes in a hierarchical fashion to compose identifiers. The following is an example of a namespace scheme for addresses within the USA that uses a hierarchy of prefixes:
```
state.county.city.zip.street.number. 
An example element in this namespace may be identified with the following:
utah.wasatch.heber.84032.main.150S.
```
See also [AN](#autonomic-namespace).

#### Non-Establishment Event
To be able to do something with the identifier, it anchors data to the key event sequence. So you can so things like issue or revoke a verifiable credential or engage in a transaction in which you give a commitment of some form to some other entity and you can anchor that commitment to the KER log and make it verifiable that way.

#### Non-transferable identifier
And identifier of which you can't rotate its controlling private key. When the private key for a non-transferable identifier become exposed to potential compromise then the identifier must be abandoned by the controller as it is no longer secure.  

The main innovation of KERI is that it provides a universal decentralized mechanism that supports *both* non-transferable and more importantly transferable self-certifying identifiers.

#### Normative
In general, we call a theory “normative” if it, in some sense, tells you what you should do - what action you should take. If it includes a usable procedure for determining the optimal action in a given scenario. [Souce](https://www.quora.com/What-is-the-difference-between-normative-and-non-normative?share=1).

#### Non-normative
A theory is called non-normative if it does not do that. In general, the purpose of non-normative theories is not to give answers, but rather to describe possibilities or predict what might happen as a result of certain actions.
[Souce](https://www.quora.com/What-is-the-difference-between-normative-and-non-normative?share=1).

#### Payload
The term 'payload' is used to distinguish between the 'interesting' information in a chunk of data or similar, and the overhead to support it. It is borrowed from transportation, where it refers to the part of the load that 'pays': for example, a tanker truck may carry 20 tons of oil, but the fully loaded vehicle weighs much more than that - there's the vehicle itself, the driver, fuel, the tank, etc. It costs money to move all these, but the customer only cares about (and pays for) the oil, hence, 'pay-load'. [source](https://softwareengineering.stackexchange.com/questions/158603/what-does-the-term-payload-mean-in-programming).

Now payload in `KERI`. The payload of an item in an `Event Log` is one the following cryptographical building blocks in KERI:
- a content digest hash 
- a root hash of a Merkletree
- a public key
Note that the KERI never puts raw data or privacy sensitive data in a `KEL` or `KERL`.

#### Prefix
A prefix that is composed of a basic Base-64 (URL safe) derivation code prepended to Base-64 encoding of a basic public digital signing key.\
Including the derivation code in the prefix binds the derivation process along with the public key to the resultant identifier. 
```
An example of the prefix with a one character derivation code and a 32 byte public key encoded into a 44 character Based-64 string follows:
BDKrJxkcR9m5u1xs33F5pxRJP6T7hJEbhpHrUtlDdhh0.
```
<img src="../images/prefix.png" alt="Prefix derivation" border="0" width="700">

#### Public Key Infrastructure
A public key infrastructure (PKI) is a set of roles, policies, hardware, software and procedures needed to create, manage, distribute, use, store and revoke digital certificates and manage public-key encryption.
<img src="../images/pubprivkey-caveat.png" alt="Public Private Key caveat to KERI" border="0" width="400"> 
[Wikipedia].(https://en.wikipedia.org/wiki/Public_key_infrastructure)

#### Race condition
A race condition or race hazard is the condition of an electronics, software, or other system where the system's substantive behavior is dependent on the sequence or timing of other uncontrollable events. It becomes a bug when one or more of the possible behaviors is undesirable. [Source](https://en.wikipedia.org/wiki/Race_condition).

#### Root of trust
Replace human basis-of-trust with cryptographic root-of-trust. With verifiable digital signatures from asymmetric key cryptography we may not trust in “what” was said, but we may trust in “who” said it.\
The root-of-trust is consistent attribution via verifiable integral non-repudiable statements.

#### Rotation Event
A type of `Establishment event` that allows to change to authoritative public key. So we start with a `root-of-trust` in public private key pair that get down to the identifier, and then we can rotate authoritatively to other keypairs given signed rotation messages. The infrastructure that we need, keeps track of these rotations, or `Key Event Receipt Infrastructure`.
_(SamMSmith)_
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

The binding in a Self-Addressing Identifier between inception data and private key can be created by replacing the public key in the identifier prefix with a content digest (hash) of the inception statement (that includes the public key). So it's a further step of commitment to identifier information and also another level of hiding information at face value by one-way encryption beyond the inception statement. However all the information is end-verifiable.

#### Self Certifying Identifier
In brief: A self-certifying identifier cryptographically binds an identifier to a key-pair.\
It is an identifier that can be proven to be the one and only identifier tied to a public key using cryptography alone.\
A controller issues an own Identifier by binding a generated public private keypair to an identifier. After this a controller is able to sign the identifier and create a certificate. Also called a _cryptonym_. The simplest form of a self-certifying identifier includes either the public key or a unique fingerprint of the public key as a `prefix` in the identifier.

<img src="../images/sci_issue_bind.png" alt="Self Certifying Identifier issuance and binding" border="0" width="400">

The root-of-trust is fully cryptographic, there is no infrastructure associated with it. If we start there we can build a secure system on top of that. It means SCI gives us strong bindings between the keypair, the controller and the identifier. And so it fixes the main weakness of any administratively issued identifier asserting the binding between the keypair and the identifier and between the controller and the identifier, replacing them with all cryptographically strong bindings.

<img src="../images/sci_ssi_book.png" alt="Self Certifying Identifier Generation and Publishing" border="0" width="400">

[Source](https://livebook.manning.com/book/self-sovereign-identity/chapter-8/v-9/141) is #SSI book.

#### Self Sovereign Identity
It is information given out by a party involved. It is empowering the individual to help governments doing their job.  With SSI a criminal can’t cheat without being caught. SSI reduces the state's expense per individual.  SSI makes tough investigation easier and false judgements rarer. The mechanism verifies automaticly and handles broken cases gracefully.

SSI is a new model for Internet-scale digital identity based on an emerging set of protocols, cutting edge cryptography and open standards. Technological and social movements have come together that make SSI possible. ([Source](https://livebook.manning.com/book/self-sovereign-identity/chapter-1/v-8/14)).\
Decentralisation of the `root-of-trust` and `verifiable credentials` come into play and delivers  “user-centric identity”: more control and self-determination of individuals, individuals machines and combinations of these, that identify as one.\
_(@henkvancann)_

#### Spanning layer
An all encompassing layer horizontal layer in a software architecture. Each trust layer only spans platform specific applications. It bifurcates the internet trust map. There is no spanning trust layer.
<img src="../images/spanning_layer.png" alt="spanning layer" border="0" width="800">

#### Subject
A digital subject: A person or thing represented or existing in the digital realm which is being described or dealt with. ([Source](https://www.identityblog.com/?p=352)).

#### Transaction Event Log
Also `TEL`: An externally anchored transactions via cryptographic commitments in a `KEL`.\
The set of transactions that determine registry state form a log called a Transaction Event Log (TEL). The TEL provides a cryptographic proof of registry state by reference to the corresponding controlling KEL.
Any validator may therefore cryptographically verify the authoritative state of the registry.
<img src="../images/TEL-and-KEL.png" alt="TEL and KEL" border="0" width="600">

#### Transfer
The process of changing the _controller_ of _cryptocurrency_, _identity_ or _verifiable credential_. MAY require the use of a _key_.

#### Transferable identifier
And identifier of which you can rotate its controlling private key. When the private key for a transferable identifier become exposed to potential compromise then control over the identifier may be transferred to a new key-pair to maintain security.

The main innovation of KERI is that it provides a universal decentralized mechanism that supports *both* non-transferable and more importantly transferable self-certifying identifiers.

#### Trust-over-IP
It's a term related to the effort of a foundation. The Trust over IP Foundation is an independent project hosted at Linux Foundation to enable the trustworthy exchange and verification of data between any two parties on the Internet. [More](https://trustoverip.org/about/faq/).
<img src="../images/trust-over-ip-stack.png" alt="Trust over IP stack" border="0" width="600">

#### Validator
a _validator_ is anybody that wants to estblish control-authority over an identifier, created by the controller of the identifier. Validators verify the log, they apply duplicity detection or they leverage somebody else's duplicity detection or apply any other logic so they can say "Yes these are events I can trust".

During validation of virtual credentials for example, a `verifier` checks to see if a `verifiable credential` (VC) has been signed by the controller of this VC using the applicable verification method.

#### Verifiable Credential
Verifiable Credentials standardize formal conversation.  VCs structure discussion between two [or more] parties, it’s private and the proofs that an indvidual has got from  an authority can’t be denied.  Every statement can be checked, and no statement can be either deleted or changed.

VC; A data model for conveying claims made by an issuer about a subject. See [vc-data-model](https://www.w3.org/TR/vc-data-model/) for more.\
Credentials are a part of our daily lives; driver's licenses are used to assert that we are capable of operating a motor vehicle, university degrees can be used to assert our level of education, and government-issued passports enable us to travel between countries. This specification provides a mechanism to express these sorts of credentials on the Web in a way that is cryptographically secure, privacy respecting, and machine-verifiable. [Know more](https://www.w3.org/TR/vc-data-model/)

#### Verifiable Data Structure
Provides proof of key state for its identifier. In KERI it is the Key Event Log (`KEL`). Key management is embedded in KELs, including recovery from key compromise.

#### W3C DID
The W3C consortium Decentralized ID standardization. [More](https://w3c.github.io/did-core/).

#### WebAssembly
WASM, or just WA) is an _open standard_ that defines a portable binary-code format for executable programs, and a corresponding textual assembly language, as well as interfaces for facilitating interactions between such programs and their host environment.\
The main goal of WebAssembly is to enable high-performance applications on web pages, but the format is designed to be executed and integrated in other environments as well, including standalone ones. [More info](https://en.wikipedia.org/wiki/WebAssembly).

#### (Digital Identity) Wallet
In our context it is software and sometimes hardware that serves as a key store and functionality. Keys can be private keys and public keys, hashes and pointers. Functionality can be signing, invoices (receive), send, virtual credentials, delegation, etc. This is the [`agency`](#agency) part of a wallet. \
[More about digital ID Wallets](https://www.thalesgroup.com/en/markets/digital-identity-and-security/government/identity/digital-identity-services/digital-id-wallet)\
[More about cryto Wallets](https://cryptocurrencyfacts.com/what-is-a-cryptocurrency-wallet/).
