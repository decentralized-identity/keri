---
tags: KERI
email: sam@samuelsmith.org
---

# Security from Zero Message Malleability

The KERI approach is that the over-the-wire serialization of the key event message is completely encompassed by the attached signatures. Likewise digests that chain one key event message to another completely encompass the over-the-wire serializaton of the chained digested key event message. We call this property zero message malleability. Moreover, because each message is signed, the signature protects the embedded chaining digest.

What this means is that if even 1 bit of the signed or digested key event message is changed the signature or digest are invalidated.  This property of zero message malleability mitigates a host of attack vectors that may referred to as transaction malleability.  An attacker may not change even one bit of an over-the-wire message without it being detected by any validator as invalid (not verifiable). Thus any successful attack by an external entity must start with compromising the signing keys of the controller in order to create a alternate version of message that is verifiable. 


In many protocols the signatures and/or digests do not completely encompass the the over-the-wire serialization but some subset of data in the key event. In these type of protocols the specification of that data subset must be precisely specified to avoid vulnerabilities. This include type, labels, and structure. If not then an attacker might be able to exploit some ambiguity in that specification to provide an alternate version of the message that still verifies with the same signature without having to compromise keys. Indeed any optional data allowed in the message that is not wrapped in the signature but that has some semantic value provides an attack vector. This semantic leakage often happens over time as the standard evolves.

The KERI approach of zero message malleability is a future proof  approach that prevents semantic leakage from ever occurring as the protocol evolves over time and provides some flexibilty with regards the specification of optional data within each message. An attacker must first compromise keys before it can play with optional data.

KERI is opinionated about security. The best practice for locking down any semantic leakage is to fully encompass the over-the-wire key event message with the signatures and digests not some subset of the data. 

This approach is somewhat inconvenient when generating the over-the-wire serializations but it is an intentional trade-off that reflects KERI's security first aesthetic.

