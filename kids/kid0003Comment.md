---
tags: KERI
email: sam@samuelsmith.org
---

# Zero Message Malleability

[![hackmd-github-sync-badge](https://hackmd.io/LdDZLLQvSxml3k3ND7jFZg/badge)](https://hackmd.io/LdDZLLQvSxml3k3ND7jFZg)

version 1.02


The KERI approach is that the over-the-wire serialization of the key event message is completely encompassed by the attached signatures. Likewise digests that chain one key event message to another completely encompass the over-the-wire serializaton of the chained digested key event message. We call this property zero message malleability. Moreover, because each message is signed, the signature protects the embedded chaining digest.

What this means is that if even 1 bit of the signed or digested key event message is changed the signature or digest are invalidated.  This property of zero message malleability mitigates a host of attack vectors that may referred to as transaction malleability.  An attacker may not change even one bit of an over-the-wire message without it being detected by any validator as invalid (not verifiable). Thus any successful attack by an external entity must start with compromising the signing keys of the controller in order to create a alternate version of message that is verifiable. 


In many protocols the signatures and/or digests do not completely encompass the the over-the-wire serialization but some subset of data in the key event. In these type of protocols the specification of that data subset must be precisely specified to avoid vulnerabilities. This include type, labels, and structure. If not then an attacker might be able to exploit some ambiguity in that specification to provide an alternate version of the message that still verifies with the same signature without having to compromise keys. Indeed any optional data allowed in the message that is not wrapped in the signature but that has some semantic value provides an attack vector. This semantic leakage often happens over time as the standard evolves.

The KERI approach of zero message malleability is a future proof  approach that prevents semantic leakage from ever occurring as the protocol evolves over time and provides some flexibilty with regards the specification of optional data within each message. An attacker must first compromise keys before it can play with optional data.

Zero transaction malleability does not prevent a malicious or faulty conroller from crafting invalid but verifiable messages or from crafting verifiable but malicious messages that expose weaknesses in the specification of the event message. But only the holder of the private signing keys may do so. And the KERI approach to duplicity detection means that a mallicious controller may not undetectably create multiple versions of a given verifiable key event message. This mitigates the risk of specification ambiguity to mallicious controllers.

KERI is opinionated about security. The best practice for locking down any semantic leakage is to fully encompass the over-the-wire key event message with the signatures and digests not some subset of the data. 

Zero message malleability is somewhat inconvenient when generating and parsing the over-the-wire serializations but it is an intentional trade-off that reflects KERI's security first aesthetic.

## Semantic Leakage

We define semantic leakage to occur whan any part of an over the wire message that contributes any meaning or function that affects the behavior of the protocol but is not wrapped in a signature. Often this might be a header or some optional part of a message. A message with semantic leakage is inherently vulnerable to probing attacks. Its just asking for trouble.

Zero Message Malleability, is a specific design feature that says completely wrap over the wire messages with a signature(s).  Many protocols employs MACs Hashes and Signatures but make optimizations that result in not wrapping the full over the wire message. This exposes them to semantic leakage. It is one of the most insidious and difficult to detect types of vulnerabilities. Bitcoin still suffers from new transaction malleability attacks as do many protocols such as SSL. Until those protocols achieve ZMM they will contintue to be vulnerable.

## Probing Attacks

In a protocol where some parts of the over the wire message (say a header or an optional block) is not wrapped by the signature, i.e. does not have ZMM, then a probe attack is enabled where an attacker can send different messages but whose signatures still verify. These different messages may elicit different responses. These become a means of discovering defects in an implementation without having to compromise keys. Compromizing keys is hard. Its not susceptible to probing attacks if those keys are full 128 bit cryptographic strength. KERI's ZMM makes such attacks, i.e. probing attacks without compromising signatures, impossible.


ZMM does not protect against a malicious controller. In KERI the duplicity detection protects against malicious controllers. A malicious controller has access to the keys and may therefore create and sign messages at will. But that controller may not create duplicitous messages without risking detection.

For example if a given validator's implementation of KERI has defects in it then a malicious controller can send messages that are fully wrapped in verifiable signatures but the contents somehow expose an error in the validators implementation. Typically incorrelty implemented validation logic. A trivial example would be non-sequential sequence numbers. If a validator's code did not check for sequential sequence numbers then it would create a malformed KEL that some other validator would reject.

## Formal Schema

One of the reasons that many protocols with flexible message structure use formal schema descriptions is to avoid vulnerabilities that may arise from inadvertent semantic leakage when the protocol does not have ZMM.  Inadvertent semantic leakage may arise over time as the protocol features are changed. We call this semantic drift.  ZMM means that inadvertent leakage is not possible, hence semantic drift is less dangerous. In spite of semantic drift a ZMM protocol is not vulnerable to external probing attack without compromise of keys.  






