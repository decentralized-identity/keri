---
tags: KERI
email: sam@samuelsmith.org
comment: Local Copy
file: kid0001Comment.md
---


# KID0001 - Commentary - Prefixes, Derivation and derivation reference tables 

[![hackmd-github-sync-badge](https://hackmd.io/AL98u-6NSlSnv0qsynZUDQ/badge)](https://hackmd.io/AL98u-6NSlSnv0qsynZUDQ)






## Navigation

[Back to table of contents](https://github.com/decentralized-identity/keri/blob/master/kids/readme.md)

| Link | Commentary | Section |
| --- | --- | --- |
| [0000](https://github.com/decentralized-identity/keri/blob/master/kids/kid0000.md) | [X](https://github.com/decentralized-identity/keri/blob/master/kids/kid0000Comment.md) | Glossary, overview, how to use |
| [0001](https://github.com/decentralized-identity/keri/blob/master/kids/kid0001.md) | X | Prefixes, Derivation and derivation reference tables |
| [0002](https://github.com/decentralized-identity/keri/blob/master/kids/kid0002.md) | [X](https://github.com/decentralized-identity/keri/blob/master/kids/kid0002Comment.md) | Data model (field & event concepts and semantics) |
| [0003](https://github.com/decentralized-identity/keri/blob/master/kids/kid0003.md) | [X](https://github.com/decentralized-identity/keri/blob/master/kids/kid0003Comment.md) | Serialization |
| [0004](https://github.com/decentralized-identity/keri/blob/master/kids/kid0004.md) | [X](https://github.com/decentralized-identity/keri/blob/master/kids/kid0004Comment.md) | Key Configuration (Signing threshold & key set) |
| [0005](https://github.com/decentralized-identity/keri/blob/master/kids/kid0005.md) | [X](https://github.com/decentralized-identity/keri/blob/master/kids/kid0005Comment.md) | Next Key Commitment (Pre-Rotation) |
| [0006](https://github.com/decentralized-identity/keri/blob/master/kids/kid0006.md) | [X](https://github.com/decentralized-identity/keri/blob/master/kids/kid0006Comment.md) | Seals |
| [0007](https://github.com/decentralized-identity/keri/blob/master/kids/kid0007.md) | [X](https://github.com/decentralized-identity/keri/blob/master/kids/kid0007Comment.md) | Delegation (pending PR by Sam) |
| [0008](https://github.com/decentralized-identity/keri/blob/master/kids/kid0008.md) | [X](https://github.com/decentralized-identity/keri/blob/master/kids/kid0008Comment.md) | Key-Event State Machine |
| [0009](https://github.com/decentralized-identity/keri/blob/master/kids/kid0009.md) | [X](https://github.com/decentralized-identity/keri/blob/master/kids/kid0009Comment.md) | Indirect Mode & Witnesses |
| 0010 |  | Recovery/consensus Algorithm (KAACE) |
| 0010 |  | Database & Storage Considerations |
| 0097 | n/a | **Non-Normative** Implementation Guidance |
| 0098 | n/a | Use Cases |
| 0099 | n/a | Test Vectors and Normative Statement Index |


## Overview

One of the most important design goals for KERI is performance in data streaming applications. This goal exhibits itself in many design choices throughout the KERI implementation. This includes asynchronous operation, support for bare metal protocols like TCP and UDP, streaming friendly envelopeless signature and receipt attachments and compact encoding of both events and cryptographic material. This document addresses specifically the compact cryptographic material encoding schemes and how they support higher performance asynchronous streaming of KERI events and attachments. 

### Asynchronous Replay of Attached Cryptographic Material

KERI is based on cryptographic proofs of control authority via verifiable hash chained signed data structures called Key Event Logs. Because almost every decision made a component of KERI requires access to one or more KELs, compact encoding of those KELs may provide significant performance benefits. But an even more compelling reason for compact encoding of cryptographic material is not just the events themselves the attached signatures and receipts to those events. The vast majority of bandwidth consumed in communications between KERI components such as controllers, validators, witnesses, watchers, jurors, and judges will be due attached signatures and receipts. These may dwarf the associated events by two orders of magnitude. This is especially true when replaying Key Event Logs (KELs) between any two components.

For example most of the cryptographic material inside an event consists of public keys, digests and identifiers. Identifiers are usually expressed as a public key or a digest. The minimum security level for KERI is 128 bits of cryptographic strength. For ECC (public, private) key-pairs, such as, Ed25519 or EcDSA secp256k1 these means 32 byte (256 bit) and 33 byte long public keys respectively. Likewise cryptographic digests (hashes) with 128 bits of cryptographic strength and post quantum resistance, such as, Blake3 or Sha3 this means 32 byte (256 bit) long digests. On the other hand the signatures for Ed25519 and EcDSA secp256k1 are 64 byte (512 bit) long. In normal operation where events are being disseminated the receipts are exchanged asynchronously in part (not all at once). But replay or cloning of a KEL will involve full streaming of all the events and attached signatures and receipts. 

Suppose an identifier uses a 3 of 5 multi-sig scheme. Each event could have up to 5 attached signatures. A public identifier could also have witnesses. Suppose the number of witnesses is 10. Thus a replay of any event could include all 10 of the the witness receipts (signatures). Finally the watcher network for any given validator may have many more watchers than witnesses and each watcher may sign their copy of the event and gossip it to the other watchers. Suppose there are 100 watchers that a validator trusts, a replay of the event log of that validator with all the watcher receipts (signatures) could include 100 watcher signatures for each event. Moreover, the attached signatures need to be identified so that they may be matched with the proper public keys. For signatures of the controller the public keys are in an ordered list so the signatures could be matched to the public key using an index into the ordered list. Likewise for witnesses in an ordered witness list. However in general for watchers (and witnesses) that use non-transferable identifiers the public key may be found in the associated identifier so a given witness/watcher signature can be matched with its public key merely by attaching the witness/watcher identifier.  Validators and other components such as jurors and judges may use transferable identifiers each with a multi-sig set of public keys. Thus attached signatures will need additional information such as a location seal into the KEL of the validator with transferable identifier in order to get the public keys.  Thus the bandwidth requirements of the replay of a given KEL with multiple identifiers may be dominated by the attached signatures and associated identifiers by at least two orders of magnitude more  than the events.  Indeed because of the different ways that public keys for the signatures may be identified, the attached receipt signatures may not be composed as a homogenous group, but may instead be composed of at least 3 groups with different signatures with different additional cryptographic material used to identifier the public keys for those signatures. 

### Composable Concatenation of Heterogenous Attachments

KERI's design goal is to provide these signatures (receipts) in a compact concatenation composable manner that is compatible with asynchronous streaming on bare metal protocols. This makes enveloping, where some set of block delimeters are used to envelope each set of attachments, a poor choice. Delimited enveloping schemes are verbose and require synchronizing the assemblage of the full enveloped attached material prior to transmission of any material. Whereas concatenated attachments may begin streaming asynchronously before all have been assembled. And heterogeneous attachment groups benefit from framing or grouping composition operators such as counters or other inserted attachments. 

Archival of streams of concatenated attachments is more reliable if that stream has a textual (text printable) representation. A textual stream representation also allows the use of system logging facilities and regular expression based text parsers to access the data in the archived textual stream even years in the future when binary libraries that support the binary format are no longer supported. An archived text stream include human readable header that includes  a text description of the streaming format.

Streaming concatenated attachments is analogous to streaming frames in many data streaming protocols such as video and audio stream protocols. Especially protocols for lossless compression algorithms [[6]][[7]]. Heterogenous composed attachments are analogous to different types of frames in these protocols and inserted grouping composition operators are analogous to framing headers. These are also called bitstream splicing operators [[7]]. One of the principal advantages of grouped framing is that a stream processor may split the stream into groups and process each group concurrently in parallel instead of processing each group serially. This allows a stream processor to use load balancing, buffering, multi-cores, etc to optimize stream processing performance. At scale this sort of group composition makes optimization relatively easy. The history of streaming protocols is replete with examples where the original design of the protocol did not anticipate parallel processing at scale resulting in extremely difficult constraints on streaming performance. Therefore efficient asynchronous replay of the attached concatenated cryptographic material for signatures and receipts is an important design constraint for KERI. Performance at scale constitutes an important domain of operation for processing attached cryptographic material in KERI.

## Cryptographic Material Encoding

Cryptographic operations require large random or pseudo random numbers. The typical representation used by cryptographic libraries is not actually a number in the strict computer sense but an array or string of bytes. In Python for example, the function parameters for cryptographic libraries expect bytes (byte string objects). Different types of cryptographic material are distinquished by the type of cryptographic material, and the crypto suite operation that is used to derive the crypto material.  The typical approach is to house the raw material together with the type and crypto suite (version) in a data structure. For example, Ed25519, is a crypto suite for digital signatures with cryptographic material types that are private keys, public keys and signatures. The associated operations are key pair creation, signing, and signature verification. The internal storage and processing of the data structure fields is usually not a limiting concern. Its only when transmitting over the wire where bandwidth constraints demand more compact representations.

### Raw Binary Material with Code

Some serializations of data structures are relatively verbose. JSON is a prime example.  High performance data streaming applications such as those that KERI intends to support would suffer greatly from such verbose serializations especially given the volume of attached signatures and receipts contemplated for KERI. There are other more compact serializations for mapping data structures such as CBOR or MSGPack but any data structure serialization is still relatively verbose when compared to compact binary representation. The over the wire serialization and representation of each cryptographic material item would benefit from a much more compact representation than a serialized mapping data structure. One way to manage this is to use context to remove many of the fields in the data structure. That is the context may be used to provide additional information about the cryptographic material derivation. Any remaining derivation information may then be compactly encoded into an indexed table.  The index may then serve as a derivation code for the cryptographic material. Each derivation code in the table may be used to represent some unique combination of derivation information that together with the context of where the code is used determine unambiguously the nature of the associated cryptographic material. Thus using context together with a derivation code table we may obtain the most compact representation practically possible. There are only a few highly performant cryptographic suites and only a few types of material in each suite. Leveraging this allows KERI to use a compact derivation code from a relatively small table, where each entry in the table combines all the essential fields from a much more verbose crypto material data structure into one code. One can always define a mapping that explodes the derivation code table into more verbose representations such as JSON Web Tokens or other similarly verbose encodings. The result is that each crypto material item may be represented by two fields, these are, the derivation code and the raw material. The derivation code may then be prefixed to the raw material to create the most compact seralization form possible. We can abstractly represent each cryptographic material item with a two element representation expressed as a tuple as follows:

*(dc, rm)*

 where *dc* represents the derivation code and *rm* represents the raw material.


### Namespace Compatibililty of Identifier Prefixes and Other Cryptographic Material


KERI is an identifier system that is meant to provide secure control over namespaces. The most widely used namespace is the URI standard which includes URNs and URLs [[2]]. URI namespaces are represented using a textual encoding. This makes it easy for human meaningful interaction and use of the name space. Humans primarily interface to computing system via text. A textual representation has the highest potential for broad or universal adoption. ASCII is the most widely adopted and supported textual representation and URIs by-in-large use ASCII compatible text representations. The more modern UTF-8 text standard has the desirable feature that non-control ASCII text (and many control characters) are identically represented in UTF-8. For similar reasons, many other important namespace standards such as file systems also use an ASCII/UTF-8 textual representation. Consequently for KERI to attain broad adoption as an identifier system, its identifiers would greatly benefit from a native textual representation. Human readable, i.e. textual representations have the broadest adoptibility possible. Also as mentioned above textual representation enable long term robustly recoverable archival of the associated documents in text form with textual identifiers.

The primary difficulty is that KERI's self certifying identifier prefixes are derived cryptographic material, that is, long strings of pseudo random bytes. Thus to express these identifiers in a text based namespace such as a URI, file system, or others we need a textual representation or encoding of the associated cryptographic material. The most practical compatible textual encoding both due to its almost univerasl support and compactness is a Base64 encoding [[3]]. Base64 maps 6 bits of raw binary data to a single ASCII printable text character. Each ASCII character uses 8 bits of binary data. So Base64 is a less compact representation that is more compatible with human meaningful namespace standards. Although a Base64 expression of a 32 byte binary array of bytes is not very memorable, it is text and can but used as part of a textual namespace such as URL or other textual namespaces such as the W3C DID standard [[4]]. The are two variants of Base64, one is plain or conventional Base64 and the other is Base64-URL for Base64 that is both URL and file safe. Base64-URL is the variant we want for namespace compatibility. 

Another important consideration is that KERI's security is largely based on cryptographic digital signatures. A signature is only verifiable against a specific serialized encoding of the signed data. Thus a signature on a raw binary string of bytes will not verify against a Base64 encoded version of the same data and vice versa. Signatures attached to data allow one to verify the authenticity of data to the controller of the private keys used to create the signature.  One important use case is for one entity to issue a signed statement to includes a reference to some other entity's identifier. Thus the representation of the other identifier in that statement is the only verifiable representation vis-a-vis that signature. Consequently, the native encoding representation of signature verifiable (authenticatable) statements may be a determining factor in what should be the native encoding or representation for KERI identifiers. Most statements used in human meaningful interactions are represented in a text, not a raw binary, encoding and the most popular text encodings are ASCII or the ASCII compatible UTF-8. Therefore the native representation for KERI identifiers should also be ASCII compatible. Moreover as mentioned above, the most compact practical choice for encoding binary as text is Base64-URL [[3]]. For the sake of simplicity, herein everywhere Base64 is referenced it is meant the URL file safe variant of Base64 unless otherwise qualified.

Another important property of Base64 is that it may be applied to convert a stream of composed items, such that, the converted stream may be converted back and decomposed without data loss. Other encodings such as Base58 Check are not composable but require each item to be parsed or framed and converted separately [[15]]. A composable stream may be dumped en mass to a text file and then parsed later with a regular expression parser. This allows archival of binary streams without parsing the stream itself prior to archival, one merely Base64 encodes the stream or any composable portion of the stream.

Given that KERI cryptographically derived identifiers are to be expressed in Base64, we must answer the question of how to map the tuple, (derivation code and raw material), that is, *(dc, rm)*, to a single string of Base64 characters. We may extend this same encoding approach to not merely self certifying identifiers but any of the cryptographic material items used in KERI. These include in addition to identifiers, public keys, private keys, digests, signatures and other items.

The choices are:

A) First prepend (concatenate) a derivation code expressed in binary to the cryptographic raw material and then convert the resultant array of binary characters to Base64. (unstable derivation code representation)

B) First convert the raw material to Base64 and then prepend the derivation code expressed in Base64 to the converted raw material. (stable derivation code representation)


We must prepend, not append the derivation code because any parser needs to knows how to interprete the appended raw material and may do this by first extracting and processing the derivation code and then extracting the remaining characters which are the cryptographic material. This is especially important if there are no delimiters or framing headers that separate one cryptographic material item from the next. We call this a *self-framing* representation. Self-framing means the derivation code itself serves as an encapsulated framing header for the appended cryptographic material item. This is a very useful feature in any data streaming protocol because it provides an extremely efficient if not the most efficient parsable representation possible. material.

Of the two choices A) or B) above, KERI has chosen the latter. The derivation code is *stable*. A *stable* derivation code representation means that the code always appears the same way no matter the value of the appended crypto material. An unstable code representation changes depending on the value of the appended crypto material. A) is unstable and B) is stable. A stable code representation in Base64 allows any text based parser such as a regex parser to parse the stream and segment the composable elements. This supports out of band archival and system logging purposes not merely the primary in band use of the cryptographic 

To understand  why one is stable and the other unstable, we must first understand how Base64 conversion works. Raw binary is represented as a string or array of bytes where each byte is an octet of 8 bits. When converting such a string of bytes to Base64, the string of 8 bit octets is subdivided into a string of 6 bit sextets. Each sextet is then converted to a single Base64 text character. 

Lets then compare what happens if we first prepend a binary derivation code and then convert the concatenated string of bytes. Suppose that the derivation code is only 1 byte. This analysis applies to any length derivation code at least with regards the trailing byte or bytes of longer derivation codes, but we consider the simple case of one byte first.

For a one byte derivation code the first six bits (1 sextet) map to a single Base64 character but the remaining 2 bits of the derivation code byte are combined with the first 4 bits of the first byte of the appended cryptographic material to form the second Base64 character. The actual Base64 character that appears as the second character changes based on the specific cryptographic material item. This means that part of the derivation code representation is not stable (hence unstable). This is an undesirable feature for readability in the name space domain. Although long strings of Base64 characters are not very human meaningful, they are still text and much more human meaningful in terms of reading and comparison that a binary representation. More importantly, the derivations codes may be short even as short as one Base64 text character. Such short codes are easily recognizeable and are helpful when reading statements that include namespace identifers or other such cryptographic material items. As a result the crypto suite and cryptographic material type may thereby be more easily recognizable. This has value when debugging and interpreting statements that include the Base64 representation of the crypto material. Thus if we want stability of the derivation code representation in the text domain then we want to use the second approach B) for mapping the *(dc, rm)*  representtion to and from the Base64 text representation. There is one case where it doesn't matter, i.e. we get stability with either approach. Recall that the least common multiple of 6 bits and 8 bits is 24 bits or 3 bytes. Any byte string that is a multiple of 3 bytes will convert to an integral multiple of 4 base64 text characters. Consequently if the derivation code in binary were constrained to always be a multiple of 3 bytes then its corresponding Base64 representation would always be a multiple of 4 Base64 characters and therefor be stable. Because the converted code is an integral number of both hextet and octets it will not mix in any bits from the appended cryptographic material. However, constraining the derivation code to be a multiple of 3 bytes (4 Base64 characters) means that we can not use a more compact 1 char or 2 character derivation code. But using the second approach enables both a stable code representation and shorter derivation codes.

Furthermore the non-integral mixing (unstable representation) of the trailing byte of the derivation code with the first byte of the cryptographic material means that text based parsers may not extract the derivation code as an integral number of Base64 charcters and then likewise extract the remaining cryptographic material as an integral number of Base64 characters. A parser must use a combination of text and binary operations (bit shifts) to extract the cryptographic material. Alternatively a parser must first convert the combined element to binary before parsing. This may be cumbersome for text based parsers. 

To conclude, stability and integral representation in the text domain indicates that the preferred approach (as selected by KERI) for mapping between the *(dc, rm)* representation and the Base64 represention is to first convert the *rm* into Base64 and then prepend an integral number of Base64 characters as the base64 derivation code. The representation of the derivation code in the *(dc, cm)* tuple could either be the base64 characters or the equivalent binary representation but in the later case then the binary *dc* would also be converted to an integral number of Base64 characters before being prepended to the Base64 *rm* characters when converting to the Base64 representation.

We can formally label this mapping as *R2T* for *Raw* binary tuple to Base64 *Text* and *T2R* for Base64 *Text* to *Raw* binary tuple.



### Streaming Binary

The final consideration is how to decide on the exact Base 64 derivation codes including code lengths. We want a code table that supports future extensibility as well. Additional considerations include other properties of the derivation codes that might be useful or valuable. One obvious additional consideration is streaming efficiency. Base64 is not as compact as binary. There is a 33% size penalty when streaming a Base64 representation of a data stream compared to the binary representation of the same stream. Base64 is 4/3 the size of the binary or 1/3 larger. As detailed above, the volume and heterogenous nature of KERI cryptographic material attachments (signatures, receipts, etc) makes very attractive the avoidance of that 33% performance penalty by defining an equivalent binary streaming representation of the associated cryptographic material.

One approach for a more compact binary streaming representation is to create a hybrid representation where the Base64 derivation code is followed by, not the Base64 version of the cryptographic material, but by the raw binary version. This majorly captures the size advantage. However a parser has no way of telling if the remaining bytes of a given cryptographic material item are in Base64 or in binary merely from the prepended derivation code. 

There are three approaches to enabling an optional parsable binary crypto material representation.

1) Have a unique derivation code for each of the two crypto material variants, Base64 and binary. But this effectively doubles the size of the derivation code table. This may become problematic over time and may result in relatively inefficient codes. 

2) Use context of where a given crypto material item appears to indicate how to parse the format of the attached crypto material (Base64 or binary). This does not incur table size doubling like option 1) above, but has the disadvantage that there may not be enough contextual information in the attached crypto material stream to always unambiguously determine the variant. This would make it difficult to generally take advantage of the size benefits of the more compact binary version.

3) Use an additional prepended contextualized composition framing code to indicate  which variant the following cryptographic material item is using, base64 or binary. This is more verbose than option 2) above but allows specifying context with a unique framing code. Each entry in the contextualized composition framing code table specifies which variant, base64 or binary follows. Furthermore in many cases the prepended composition framing code may be applied to a contiguous group of similarly composed cryptographic material items that then amortize the increased size of one framing code. This option provides a beneficial compromise between 1) and 2).


The preferred approach is 3) above. To restate, the approach is to use additional prepended contextualized composition framing codes to allow composition of groups of cryptographic material that may, depending on the framing code used, be either Base64 or binary variants. This allows composition of heterogenous cryptographic groups that may use, either the more verbose Base64 or the more compact binary representation for streaming the attached material over the wire or to storage. 

#### Composition Property

There is however one remaining complexity in choosing the composition approach to framing, that is how flexible and extensible or conversely how rigid and limited are the compositions. Clearly prepending a framing code to each cryptographic material item merely to indicate binary or Base64 is not very attractive. It makes more sense to prepend a framing code to a group of items. The complexity is that a transformation of a group of crypto material items formed by concatenation in either the Base64 domain or the binary domain does not necessarily preserve the integrity of individual items at the byte level when the group of items is converted as a group. So framed groups cannot be efficiently framed and parsed as a group nor parsed as groups and processed in parallel, but must always be parsed sequentially as individual items. Indeed we re-encounter here, the same problem described above, where bits from the trailing byte of one member of the group may become mixed with bits from the leading byte of the next member of the group unless each member is separately and sequentially converted (i.e. not as a contiguous group). This is because of the misalignment between the 6 bit sextet segmentation in Base64 character streams with the 8 bit octet segmentation in binary byte streams.


In streaming protocols the ability to flexibly compose frames of items that respect byte boundaries and to inject other frames or recompose frames into sub frames enables flexibility, extensibility, and concurrency in processing. Without this property, performant stream processing becomes more difficult when one wants to convert, compress, divert, archive, unarchive, or otherwise optimally manage streams. Flexible composition (framing) allows for  both in-stream and out of band re-composition that is analogous to operations employed in bitstream splicing and lossless streaming data compression [[6]][[7]]. Flexible re-composition is also helpful in load balancing, routing, logging, and quality of service stream processing. A useful analogy is the convolution theorem from signal processing [[5]]. The convolution theorem states that convolution in the time domain corresponds to multiplication in the frequency domain and vice versa [[5]]. Multiplication and convolution are two different composition/decomposition operations that enable powerful efficient signal processing algorithms when used in the most convenient domain (frequency or time).
In this case, we have much simpler composition/decomposition operations, these are simply concatenation/de-concatenation in both the text (Base64) and binary domains. 

To better formalize the discussion, let the term *primitive* refer to an atomic element that that may be composed/decomposed via concatenation in a stream. Conversion of any concatenated composition of any set of *primitives* in a stream between one domain and the other must always respect *primitive* boundaries at the byte level after the conversion. This means 8 bit binary octets in binary, and 8 bit Base64 characters that represent 6 bit sextets in text. Flexible parsing of concatenated compositions is enabled when both byte and character boundaries of each *primitive* are preserved in each domain after converting streams of concatenations in groups between each domain, text and binary.

Lets label the streaming binary representation *S* and the streaming Base64 text representation *T*. Then we have two mappings *S2T* and *T2S*. Or more compactly *S* for *T2S* and *T* for *S2T*. We can also symbolize the two different representations with a superscript *s* for streaming binary and  *t* for streaming Base64 text on a variable, say *x* that in turn represents a given primitive as follows:


<a href="https://www.codecogs.com/eqnedit.php?latex=x_{}^{t}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?x_{}^{t}" title="x_{}^{t}" /></a>

and

<a href="https://www.codecogs.com/eqnedit.php?latex=x_{}^{s}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?x_{}^{s}" title="x_{}^{s}" /></a>.

And the transformations between the *T* and *S* domains may be represented as follows:


<a href="https://www.codecogs.com/eqnedit.php?latex=x_{}^{t}&space;=T\left&space;(&space;x_{}^{s}&space;\right&space;)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?x_{}^{t}&space;=T\left&space;(&space;x_{}^{s}&space;\right&space;)" title="x_{}^{t} =T\left ( x_{}^{s} \right )" /></a>

and

<a href="https://www.codecogs.com/eqnedit.php?latex=x_{}^{s}&space;=S\left&space;(&space;x_{}^{t}&space;\right&space;)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?x_{}^{s}&space;=S\left&space;(&space;x_{}^{t}&space;\right&space;)" title="x_{}^{s} =S\left ( x_{}^{t} \right )" /></a>.



If we let '*+*' represent concatenation then the simplest expression of the primitive preserving composition property is as follows:


<a href="https://www.codecogs.com/eqnedit.php?latex=x_{}^{t}&plus;y_{}^{t}&space;=T\left&space;(&space;x_{}^{s}&plus;y_{}^{s}&space;\right&space;)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?x_{}^{t}&plus;y_{}^{t}&space;=T\left&space;(&space;x_{}^{s}&plus;y_{}^{s}&space;\right&space;)" title="x_{}^{t}+y_{}^{t} =T\left ( x_{}^{s}+y_{}^{s} \right )" /></a>

and

<a href="https://www.codecogs.com/eqnedit.php?latex=x_{}^{s}&plus;y_{}^{s}&space;=S\left&space;(&space;x_{}^{t}&plus;y_{}^{t}&space;\right&space;)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?x_{}^{s}&plus;y_{}^{s}&space;=S\left&space;(&space;x_{}^{t}&plus;y_{}^{t}&space;\right&space;)" title="x_{}^{s}+y_{}^{s} =S\left ( x_{}^{t}+y_{}^{t} \right )" /></a>.


We may generalize concatenation composition so that any number of primitives can be composed by using the summation operator over a subscripted variable as follows:



<a href="https://www.codecogs.com/eqnedit.php?latex=\sum_{i=0}^{N-1}x_{i}^{}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\sum_{i=0}^{N-1}x_{i}^{}" title="\sum_{i=0}^{N-1}x_{i}^{}" /></a>.

The resulting general expression for primitive preserving concatenation composition is as follows:



<a href="https://www.codecogs.com/eqnedit.php?latex=S\left&space;(\sum_{i=0}^{N-1}x_{i}^{t}&space;\right&space;)&space;=\sum_{i=0}^{N-1}x_{i}^{s}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?S\left&space;(\sum_{i=0}^{N-1}x_{i}^{t}&space;\right&space;)&space;=\sum_{i=0}^{N-1}x_{i}^{s}" title="S\left (\sum_{i=0}^{N-1}x_{i}^{t} \right ) =\sum_{i=0}^{N-1}x_{i}^{s}" /></a>

and

<a href="https://www.codecogs.com/eqnedit.php?latex=T\left&space;(\sum_{i=0}^{N-1}x_{i}^{s}&space;\right&space;)&space;=\sum_{i=0}^{N-1}x_{i}^{t}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?T\left&space;(\sum_{i=0}^{N-1}x_{i}^{s}&space;\right&space;)&space;=\sum_{i=0}^{N-1}x_{i}^{t}" title="T\left (\sum_{i=0}^{N-1}x_{i}^{s} \right ) =\sum_{i=0}^{N-1}x_{i}^{t}" /></a>.


Now given that binary streams are composed of bytes each representing 8 bits (octet) and Base64 text streams are composed of ASCII text characters of size 8 bits but each represents only 6 bits (sextet) then the concatenation composition property is satisfied if any primitive in binary has a length that is an integer multiple of 3 bytes and any primitive in Base64 has a length that is an integer multiple of 4 Base64 text characters. This is because 24 bits is the least common multiple of 8 bits and 6 bits respecively. And 24 bits is represented by 3 binary bytes or 4 Base64 text characters. To satisfy the composition property, any primitive must therefore align on 24 bit boundaries. Otherwise some bits from the preceding primitive's trailing byte become mingled with bits from the succeeding primitive's leading byte. In that case, a stream parser cannot cleanly segment one primitive from the next along byte or character boundaries but must process both primitives together. This may become extremely cumbersome and as a result entirely problematic in high performance streaming applications of KERI.

#### Direct Primitive Conversion to Binary from Stable Code Textual

With composition a stream consisting of a group primitives may be converted as a group. Let's consider what happens when we directly convert a Base64 text based primitive  to streaming binary where the derivation code is expressed as an integral number of Base64 characters and is prepended to the Base64 conversion of the raw binary crypto material. In other words we are mapping from *R* to *T* to *S*. In *R* we have a tuple *(dc, rm)*. In *T* a Base64 character string where the first character or characters are the derivation code, *dc*, and the remaining characters are the Base64 conversion of *rm*. In *S* a binary byte string where the first sextet (6 bit) or set of sextets (multiples of 6 bits) are the binary equivalents of the Base64 *dc* and the remaining sextets are the binary equivalents of the Base64 crypto material *cm*.  The mapping path looks like this,

*(dc, rm)* to *T* to *S*.

As described above, this is the approach that results in stable derivation code characters in the textual domain. 

Lets further also suppose that each primitive in the Base64 textual domain consists of a stable derivation code plus appended Base64 crypto material and has a combined length that also satisfies the composability property. This means that the combination, i.e. the primitive, has a length that is an integer multiple of 4 (Base64 characters). So we satisfy both code stability and composability.

The presence of the derivation code as part of the primitive indicates the crypto suite used to derive the crypto material. We call this *fully qualified* or *qualified* crypto material. The derivation code is the qualifier. When a composable fully qualified primitive in Base64 text domain, *T*, is converted as a whole to the binary streaming domain, *S*, the converted primitive is also *fully qualified*. It retains the derivation code but in a binary form. 

Standard Base64 implementations append pad characters to any conversion from binary to Base64 to ensure that the length of the converted primitive is a multiple of 4 Base64 chars. In other words a standard Base64 conversion is designed to provide composability in the Basee64 domain. Many uses of Base64 do not benefit from composability and in those applications the pad characters may be removed. If the application can ensure that the converted primitive will always appear in a framed or delimited manner such that a concatenated group of successive primitives would never be converted back to binary as a group, then one may ignore the pad characters. But in the case of KERI where we see a benefit from composablity, we can prepend a derivation code of the appropriate length to any converted Base64 material item to ensure that the resulting primitive is composable without using pad characters. This is done by ensuring that the combination of derivation code plus appended crypto material has a length that is an integer multiple of 4 Base64 characters.   

Any crypto material in bytes that is not an integer multiple of 3 bytes will convert to standard Base64 with either 1 or 2 pad characters but never 3. This is because division by three may leave 1, 2, or 0 as a remainder. A remainder of 1 octet (8 bits) requires two sextets (2 * 6 = 12 bits) to fully capture all its bits. The remaining 4 bits in the 2 sextets are pad bits (not bytes or characters). But 2 sextets is not an integer multiple of 4 so two additional pad characters are required to get to 4. Thus a one byte remainder encodes to 4 Base64 characters of which 2 are pad characters. A remainder of 2 octets (2 * 8 = 16 bits) requires 3 sextets  (3 * 6 = 18 bits) to fully capture all its bits. One additional pad character is required to get to 4 characters total. Thus a two byte remainder encodes to 4 Base64 characters of which 1 is a pad character.  Therefore a binary to base64 conversion of a byte string that preserves composability may have 0, 1, or 2 pad characters that correspond respectively to a reminder of 0, 2 or 1 bytes when the number of bytes in the string is divided by 3.  

Recall that a derivation code that is an integral multiple of 4 Base64 characters will map to an integral multiple of 3 binary bytes. That is the uninteresting case. The interesting case is a derivation code that is not an integer multiple of 4 Base64 characters. The simplest case is a derivation code that is one Base64 character. This is useful if the crypto material converts to Base64 with one pad character because the pad character can be stripped off and the code prepended to make the length of the combination an integral multiple of 4 Base64 characters which will in turn convert to an integer multiple of 3 bytes.   

The simplest case looks like this. We start with dc = 1 Base 54 character and rm = 2 bytes. The raw material rm converts to 4 Base64 characters including 1 pad character. Removing the pad character and prepending the dc gives a textual representation with 4 Base64 characters. The minimum size possible that also satisfies the composablity property.  

Converting the combined primitive as a whole to binary from Base64 results in 3 binary bytes, also the minimum size possible that also satisfies the composablity property. The layout in bits of this converted form is as follows:  

6 bits provide the binary version of the dc, 16 bits are the raw binary, 2 bits of padding. The act of prepending a dc character effectively shifted the raw binary to the left by 2 bits. We must parse this result as binary with bit fields. This is not as convenient as parsing without bit fields but not uncommon for binary packet protocols especially. It is not unreasonable or uncommon to expect a binary protocol parser to deal with bit fields whereas it would be unreasonable to expect a text domain parser to deal with bit fields. To convert to (dc, rm) form from this binary form we must first mask off or extract the first 6 bits. These we convert through the standard Base64URL table back to the 1 character dc code. The remaining 18 bits are shifted 2 bits to the right. The last two bytes are the rm. Thus conversion back to (dc, rm) form involves extracting a 6 bit field and a shift.  

Similarly for a 2 character dc, conversion involves extracting 2 6 bit fields and shifting 4 bits to the right.   

Finally for a 4 character dc, conversion involves extracting 4 6 bit fields or 3 bytes and no shifts.  

Any longer dc codes when combined with the converted cm  that result in primitives  in the textual domain that are both minimally sized and also satisfy the composition property must be of the following lengths 1, 2, 4, 5, 6, 8, 9, 10, 13 .... where the length of the dc code is determined by the number of pad bytes for the converted crypto material. We then have as a result another mapping pair. These we label *S2R* and *R2S* for streaming binary to raw binary and raw binary to streaming binary. In other words *S2R* goes from a streaming binary primitive to a tuple of *(dc, rm)* and *R2S* goes from a tuple *(dc, rm)* to a streaming binary primitive. This allows us to go full circle in either direction between the 3 formats. These paths are as follows:

*(dc, rm) -> R2T -> t -> T2S -> s -> S2R -> (dc, rm)*   

and  

*(dc, rm) -> R2S -> s -> S2T -> t -> T2R -> (dc, rm)*.  

The important properties are that conversion to from S and T domains is composable via concatention over the Base64 to/from binary conversion. We have stable code representations in T for readability and textual parsing. The stable codes enable the minimum sized composable primitives.


#### Direct Primitive Conversion to Binary from Unstable Textual Code

Here we make a comparison to alternative A) which we label the unstable derivation code representation. Suppose for comparison that an unstable representation also satisfies the composablity property that is the combined code plus cryptographic material must be an integer multiple of 3 binary bytes and its dual representation in Base64 is an integer multiple of 4 Base64 characters. Similarly to B) the derivation code may be small, as little as 1 or 2 bytes. But regardless, in order to satisfy composablity, the minimum possible total size of the combined primitive is still the same as A). So there is no size advantage of an unstable version over the stable version given they both satisfy composability. The unstable version, however, has more code space because each code byte has available to it a full octet (8 bits) not merely a sextet (6 bits) per each Base64 code character. But as we will discuss below the full code space may not be usable if a parser needs to disambiguate between binary and Base64 streams or to parse otherwise unframed cryptomaterial. Self-framing becomes more difficult in the text domain. 

Lets walk through equivalent examples but for an unstable coding scheme. Suppose we have a 1 byte derivation code and 2 bytes of crypto material. The combined primitive is 3 bytes which converts as a whole to 4 Base64 characters. The code is split between the first two Base64 characters with the first 6 bits of the 1 byte code represented by the first Base64 character and the last 2 bits are mixed with the first 6 bits of the appended crypto material to provide the second character. The second character is unstable because its mixed and there is no way to predict the mixing because cryptomaterial is by nature pseudo random. The first character is also unstable in the sense that there are 4 different codes in the the 1 byte code table that share the first 6 bits. The only way to disambiguate is to either limit the code table to only use the first bits bits and treat the last 2 bits as padding. Or to extract both characters and do the appropriate bit field extraction and mapping. But this defeats the point of doing textual parsing. Consequently the typical approach is to always first convert the full primitive from Base64 back into binary. The the code byte or bytes may be simply extracted (they are stable in binary) and the remaining bytes are the crypto material. But this requires either framing or delimitation in the Base64 domain (which is the usual case but not very useful for KERI which wants self-framing in both binary and Base-64) or the Base64 to Binary takes a 4 character chunk and then converts that to three binary bytes and then from that chunk is able to determine how many more chunks are needed to get the full derivation code. If it is also assumed that the derivation code is not extensible then the number of bytes may be fixed and therefore the number of characters that need to be extracted to parse is also fixed. The advantage of the unstable approach is that once converted back to binary there are  no bit field shifts required. Thus the the composable binary representation is simpler to parse. The disadvantage of the unstable approach is that parsing effectively must happen in the binary domain. Extensible variable length derivation codes, however, may be more difficult to parse and may be no less difficult than stable coding schemes.


### Comparative Examples

For example, did:key uses an essentially unstable approach its derivation code for its identfiers [[13]] but makes it stable (in the text domain) by prepending the character z to its derivation code and then the remaining bytes of its derivation code may only using printable text entries from the Multicodec table [[10]][[11]][[12]]. So by limiting its code space to text printable entries it has stability in the text domain. The remaining crypto material is encoded in Base58Check which as mentioned previously is not composable like Base64 [[15]]. The minimum code size is 4 bytes that are also  4 printable text characters. So its minimum size is greater. Because the did:key scheme does not satisfy the composability constraint each identifier must always appear in a framed or delimited context but it is self-framing so it may be converted on a primitive by primitive basis but not as a composed group. It appears from the did:key spec that there is no contemplation that did:key identifiers would ever be used in a streamed binary application but would only ever appear in the text domain and then converted to binary not for streaming but to perform cryptographic operations. To restate, it not composable in the textual domain although it is stable. The did:key approach exposes some of the problems with Multicodec which has some codes that are text printable and some that are not. As a result one can only use part of the Multicodec code space when designing a protocol and as a further result the minimum code size is larger than a more uniformly more compactly designed code approach.

Similarly did:peer uses a stable approach where the derivation code is expressed using some text printable characters followed by a Base58Check encoding of the raw cryptographic material [[14]]. It has comparable properties of longer minimum code size, stability given a subset of the MultiCodec table and is not composable. It also appears from the did:peer spec that there is no contemplation that did:peer identifiers would ever be used in a streamed binary application but would only ever appear in the text domain and then converted to binary not for streaming but to perform cryptographic operations.

Neither did:key nor did:peer anticipate using similarly compact prepended derivation code representations for representing other crypto material items such as digests, signatures, public keys etc. Clearly such a scheme could be developed for either but nonetheless would not be composable. Moreover given that neither did:key nor did:peer are designed to provide a more compact binary representation for their identifiers much less any other crypto material they are not useful for KERI.

## Summary

KERI's design both requires and benefits from a universal compact encoding for all cryptographic material items with stable self-framing textual derivation codes.  This compact encoding scheme fully supports both textual and binary streaming applications of attached crypto material of all types. This approach includes composability in both the textual and binary streaming domains. The primitives may be the minimum possible but still composable size. Making composablity a guaranteed property allows future extensible support of new compositions of streaming formats based on pre-existing core primitives and compositions of core primitives. This enables optimized stream processing in both the binary and text domains.


Cryptographic material in KERI has three primary representations or domains. These are as follows:

1- Separated code and raw material for crypto operations expressed as a tuple *(dc, rm)*, where *dc* is the derivation code and *rm* is the raw binary crypto material. Cryptographic operations demand the raw binary while the derivation code indicates what crypto suite of operations to use. This is the best representation for performing the cryptographic operations. We label this the *'R'* domain for raw binary material for crypto operations.

2- Test based primitive composed of a prepended base64 code and appended base64 crypto material. This is used in namespaces and is the identifier native domain but also supports text streaming replay transmission and storage. Base64 is the best practical representation for namespace compatibility and usability. We label this the *'T'* domain (for text).

3- Compact streaming binary primitive composed of a prepended binary code and appended binary crypto material. This supports efficient binary streaming replay transmission and storage. This binary compact representation is the best representation for transmission and storge efficiency. We label this the *'S'* domain for streaming binary.

Moving between these three domains involves conversion between the three representaions. These conversion we label with the respective domains labels as follows:

*R2T* and *T2R* for moving between the *R* and *T* domains.  
*T2S* and *S2T* for moving between the *T* and *S* domains.  
*S2R* and *R2S* for moving between the *S* and *R* domains.  

These give the following conversion paths:

*(dc, rm) -> R2T -> t -> T2S -> s -> S2R -> (dc, rm)*  

and

*(dc, rm) -> R2S -> s -> S2T -> t -> T2R -> (dc, rm)*.  



The mutual composiblity property of primitives in the *T* and *S* domains under the *T2S* and *S2T* conversions allows conversion of any arbitrary streaming composition of primitives as a group that maintains primitive boundaries after group conversion. This provides flexible support for performant streaming and conversion in either domain.

We can represent the relationships in a diagram that shows the circular conversion paths between domains.

![](https://i.imgur.com/WksTJXB.png)



## Composition Operators

Recall as discussion previously, that we selected option 3) as the approach to take to enable parsing of contextualized composable framing of both Base64 text and binary streams of primitives. This approach is to use contextual composable framing operators that specify if the following group of primitives is expressed as Base64 or binary. The composition or framing operators are essentially composable codes with no crypto material. Therefore each composable framing code must be a integer multiple of 4 Base64 characters or equivalently an integer multiple of 3 binary bytes. Framing is just a group count. The count is of the type of item being counted that constitutes a group and the domain that the group is represented in, that is, text or binary. The group type may be simply bytes or characters or more complexly primitives, or groups of primitives. A composable framing code is thus a typed counter of the immediately following composed group.

### Hetrogenous Attached Crypto Material Groups

With composable typed counters we may encode any combination of the typed groups and freely transform the groups between the Base64 text (namespace) domain and the more efficient binary domain. This provides future extensibility in the types of heterogenous groups of attached crypto material that may be supported for the replay of KELs/KERLs. 

### Native Composable Encoding of Messages.

Moreover, this capability may be used to define a native binary encoding for KERI messages. Currently messages are expressed as mapping objects that contain fully qualified Base64 encoding of the included crypto material items and those mappings may be futher encoded into either JSON, CBOR, or MsgPack representations. But because the included crypto material items are Base64, even the more compact CBOR and MsgPack encodings are not as compact as a native binary message encoding where all crypto material is encoded in fully qualified binary representations. If appropriate composable framing codes are defined for the elements and groups of elements in a message then we could define a native Base64 encoding that would convert one-to-one to an equivalent but even more compact native binary encoding of that message. The converted version would include fully qualified binary variants of its crypto material elements. Both the Base64 and more compact encoding would satisfy the composability property. This would allow a fully Base64 text based representation of a message stream (messages plus attachments) to be converted en mass to and from binary. The binary version of the stream for transmission and the Base64 for textual processing, human readable interpretation, logging, and archival. This specification is a future work item for the KERI protocol.

### Cold Start Stream Parsing Problem

When processing streams a parser may become confused especially if a portion of the stream is malformed in some way. This usually requires a cold start to resynchronize the parser to the stream elements. In TCP a cold start usually means closing and then reopening the TCP connection. This flushes the TCP buffers and send a signal to the other end of the stream that may be interpreted as a restart or cold start. In UDP each packet is individually framed but a stream may be segmented into multiple packets so a cold start may require an explicit ack or something to force a restart. 
After a cold start a stream processor looks for framing information to know how to parse groups of elements in the stream. If that framing information is ambiguous then the parser may become confused and require a cold start. A well designed and efficient streaming protocol provides framing information in compact form.

### KERI Message Parsing

Currently in KERI after a cold start, a stream starts with message data encoded as a mapping in JSON, CBOR, or MGPK (MsgPack). The message data includes a unique version string as the first element or field in the mapping. Each encoding has a variable but bounded number of framing characters or bytes that appear before the actual message string. In JSON these are the delimiters for a mapping followed by the version string label and delimited version string [[16]]. In JSON white space is not normative so a compliant JSON encoding may have interspersed white space [[16]]. In CBOR and MGPK the framing characters include the mapping object type and length code, and then the string label type and length code and the string type and length code [[17]][[18]]. The codes vary depending on the number of elements in the mapping and the size of the strings [[17]][[18]]. Thus in either CBOR or MGPK there is no single fixed sequence of framing bytes that may appear before the version string  Whereas a JSON encoding, without whitespace may have a fixed number of delimiting characters. But this may be a fragile dependency. The way KERI solves this parsing ambiguity is to use a regular expression, (regex), that searches the first few bytes or characters of a message encoding to match against the appropriate version string for each encoding. The version string has sufficient uniqueness that it may not be confused with any other legitimate bytes or characters at the beginning of a message. The version string also includes the total number of bytes or characters in the encoded message data mapping so a parser may know how many bytes to extract from the stream in order to perform the conversion from the encoded serialized mapping to the associated  message data structure. 

#### Attached Crypto Material

KERI supports the asynchronous attachment of signatures without an envelope for performance reasons. The serialized message data mappings are cryptographically signed so should any information about attached signatures be conveyed in the message then the signed bytes must change as well, thereby locking the exact set of attached signatures to a given message serialization. This is problematic for threshold multi-sig where the many different but valid sets of attached signatures are possible. Support for threshold multisig means that in KERI the message data itself must not contain any information about the attached signatures or any attached crypto material. Doing so would change the signed material and force fully synchronous transmission of messages with the exact signature set specified in the message itself or require an envelope to attach the signatures as a set to the message. In asynchronous streaming without an envelope, a parser needs separate framing information about the composition of attached crypto material. 

Some transport protocols provide facilities for attaching flexibly composed sets of crypto material. For example, one may use headers in HTTP. A custom KERI HTTP signature header, for example, could be used to attach any number of signatures to the message contained in the HTTP body. Likewise a custom HTTP header could be defined for any type of attached crypto material, thus removing the need to use framing codes when transporting over HTTP. But bare metal protocols like TCP and UDP provide no such comparable framing capabilities for attachments and hence the need for the KERI protocol to define compositional framing codes to support bare metal protocols like TCP and UDP.

The most common use case for attachments to a serialized message data mapping is  indexed attached signatures. Indexed signature primitives are fully qualified. Each derivation code in the attached signature includes the crypto suite type and the index of the public key from the associated key state that is authoritative for the associated message data. All that is needed for the parser is to frame the set of attached signatures via a counter code that indicates to the parser the number of signatures in the following group. Because each primitive is self-framing, the count code only needs the count and the domain, Base64 or binary, of the fully qualified indexed signature primitives. 

If all message streams consisted of nothing but an encoded message followed by a primitive count code and a set of attached signatures then the parser could assume that immediately following the set of attached signatures is another message composed of a serialized message data mapping and then a count code and then attached signatures. However in replay of messages the attachments may be multiple groups of different types of attachments. Consequently it would be most helpful to the stream parser to be able to determine if after some framed group there is another framed group or a new message in the stream.

#### Unique Start Bits

The easy solution is to use a framing code before each serialized message data mapping that indicates to the stream parser that a new message has started. A more elegant more compact solution would be to select framing codes whose start bits were entirely distinct from the start bits for all three of the serialized encodings, JSON, CBOR, and MGPK. In addition the start bits of the framing codes should mutually distinct for both the Base64 version and the binary version of the framing code. This way a parser could tell if the framing code itself is in Base64 or binary and thereby know how to interpret and parse the framing code itself. This provides an in-stream cold start like capability. This last feature would provide the analogous capability to a UTF Byte Order Mark (BOM) that allows a parser of UTF encoded documents to determine if the UTF codes are big endian or little endian [[19]]. But in the KERI case this feature would enable a stream parser to know if a count code is expressed as Base64 or binary and parse appropriately.

Lets examine the start bits for JSON, CBOR, and MGPK encoded mapping objects to see if this is even possible [[16]][[17]][[18]].  

Amongst the codes for mapping objects in the three serialization only the first three bits are fixed and not dependent on mapping size. In JSON a serialized mapping object always starts with "{". This is encoded as 0x7b. the first three bits are 0b011. In CBOR the first three bits of the major type of a serialized mapping object are 0b101. In MsgPack there are three different mapping object codes. The FixMap code starts with `0b100`. Both the Map16 code and Map32 code both start with `0b110`.

So we have the set of used tritet start bits (3 bits) in numeric order of `0b011`, `0b100`, `0b101`, and `0b110`. This leaves `0b000`, `0b001`, `0b010`, and `0b111` available to use for framing code start bits. In Base64 there are two codes that satisfy our constraints. These are `-` and `_`. The dash character is encoded as `0x2d`. Its first three bits are `0b001`. The underscore character is encoded as `0x5f`. Its first three bits are `0b010`. Both of these are distinct from the first three bits of any of the JSON, CBOR, and MGPK encodings. Moreover the first three bits of the corresponding Base64 binary encodings of `-` and `_` are both `0b111` which is also distinct from the all the others. Base64 maps `-` to position 62 or `0o76` (octal) and "_" to position 63 or `0o77` (octal). This gives us two different characters we can use for the first character of any framing codes. This also means we can have two different classes of framing codes. This also provides a BOM like capability to determine if a framing code is expressed in binary or Base64 [[19]]. If a framing code starts with `0b111` then its in binary format, `qb2`, and the parser knows how to convert the first sextet of the framing code. If on the other hand it starts with either `0b001` or `0b010` then its in text Base64, `qb64`, and the parser likewise knows how to convert the first character (octet) of the framing code.


#### Stream Parsing Rules

Given this set of tritets (3 bits) we can express a requirement for well formed stream start and restart.

Each stream must start (restart) with one of four things:

1) A framing code in either Base64 or Binary.
2) A JSON encoded mapping.
3) A CBOR encoded Mapping.
4) A MGPK encoded mapping. 


A parser merely needs to examine the first tritet (3 bits) of the first byte of the stream start to determine which one of the four it is. When the first tritet indicates its JSON, CBOR, or MGPK, then the included version string provides the remaining and confirming information needed to fully parse the associated encoded message. When the first tritet is a framing code then, the remainder of framing code itself will include the remaining information needed to parse the attached group. The framing code may be in either Base64 or binary. At the end of the stream start, the stream must resume with one of the 4 things, either a new JSON, CBOR, or MGPK encoded mapping or another framing code expressed in either Base64 or binary.

This provides an extremely compact and elegant stream parsing formula that generalizes to all KERI messages and attached crypto material. We now merely need to define framing codes for the appropriate attachment types to build an extensible streaming protocol that also satisfies the composability property in both the Base64 and binary domains. These codes may include ones that support a new extensible fully composable ultra compact fully qualified binary message encoding.


##  Derivation Codes

### Framing Codes

There are two families or classes of framing codes. The first class are count codes for composition of groups of crypto material primitives and they all start with the dash, `-`, character in Base64. The second class are opcodes and they all start with the underscore, `_`, character in Base64. This second class, opcodes, are yet to be defined. Their purpose is to provide future support for custom scripted processing and verification of attached signatures or other related cryptographic material. This may include, for example, collective or group signatures [[35]][[36]][[37]]. These codes would enable a compact representation of such a signature processing language. An example of a language that might be encoded this way is the Crypto Construction Language (CCLang) [[20]]. In general these opcodes are reserved to provide future support for custom processing of attached crypto material with something analogous to Bitcoin's pay-to-script-hash capability [[21]].

The current count code table has two entries in it. A newly proposed expanded table of count codes (see below), keeps the first code from the old table but removes the second code. The old second code function is now obsolete. The second code specified a domain switch to streaming binary, `qb2`, of the attached counted group. However the revised stream start/restart rules described above allow a parser to use the domain that the count code appears in, text Base64, `qb64`, or binary base2, `qb2`, to indicate the domain that the attached group much also appear in. To clarify, the attached group's domain, `qb64` or `qb2`, must always match the preceding count code's domain. This removes the need for domain specific codes that switch domains. A stream may switch domains mid stream but a group may not switch domains mid-group. Mid group switching  would break composability of the group. A special domain switching count code could only appear at the top level of a stream anyway, but the new stream restart rules now allow domain switching at the top level without special domain switching codes. This simplifies the table and removes complexity from the parsing logic without loss of generality. To restate, removal of domain switching codes is enabled by the fact that with the new stream restart rules, a stream parser can unambiguously detect which domain a composition code is encoded in, either, `qb64` or `qb2`. The Table below is for composition in the `qb64` domain. An equivalent dual binary table of sextets (octal)  would allow direct composition in the `qb2` domain. 



| Count Code | Description                                                                    | Max Count     | Chars qb64 | Bytes qb2 |
|:----------:|--------------------------------------------------------------------------------|---------------|------------|-----------|
|       **-A**## | Count of attached qualified Base64 indexed controller signatures                   |         4,095 |          4 |         3 |
|       **-B**## | Count of attached qualified Base64 indexed witness signatures                      |         4,095 |          4 |         3 |
|       **-C**## | Count of attached qualified Base64 nontransferable identifier receipt couples      |         4,095 |          4 |         3 |
|       **-D**## | Count of attached qualified Base64 transferable identifier receipt quadruples      |         4,095 |          4 |         3 |
|       **-U**## | Count of qualified Base64 groups or primitives in message data                     |         4,095 |          4 |         3 |
|       **-V**## | Count of total attached grouped material qualified Base64 4 char quadlets          |         4,095 |          4 |         3 |
|       **-W**## | Count of total grouped message data material qualified Base64 4 char quadlets      |         4,095 |          4 |         3 |
|       **-X**## | Count of total grouped message data + attachments qualified Base64 4 char quadlets |         4,095 |          4 |         3 |
|       **-Y**## | Count of qualified Base64 groups or primitives in group (context dependent)        |         4,095 |          4 |         3 |
|       **-Z**## | Count of grouped material qualified Base64 4 char quadlets (context dependent)     |         4,095 |          4 |         3 |
|       **-a**## | Count of anchor seal groups in list                                                |         4,095 |          4 |         3 |
|       **-c**## | Count of config traits (each trait is is a 4 char quadlet)                         |         4,095 |          4 |         3 |
|       **-d**## | Count of digest seal Base64 four char quadlets in digest (d)                       |         4,095 |          4 |         3 |
|       **-e**## | Count of event seal Base64 four char quadlets in triple of (i, s, d)               |         4,095 |          4 |         3 |
|       **-k**## | Count of keys in list                                                              |         4,095 |          4 |         3 |
|       **-l**## | Count of location seal Base64 four char quadlets in quadruple of (i, s, t, p)      |         4,095 |          4 |         3 |
|       **-r**## | Count of root digest seal Base64 four char quadlets in  root digest (rd)           |         4,095 |          4 |         3 |
|       **-w**## | Count of witnesses in list                                                         |         4,095 |          4 |         3 |
|   **-0U**##### | Count of qualified Base64 groups or primitives in message data                     | 1,073,741,823 |          8 |         6 |
|   **-0V**##### | Count of total attached grouped material qualified Base64 4 char quadlets          | 1,073,741,823 |          8 |         6 |
|   **-0W**##### | Count of total message data grouped material qualified Base64 4 char quadlets      | 1,073,741,823 |          8 |         6 |
|   **-0X**##### | Count of total group message data + attachments qualified Base64 4 char quadlets   | 1,073,741,823 |          8 |         6 |
|   **-0Y**##### | Count of qualified Base64 groups or primitives in group (context dependent)        | 1,073,741,823 |          8 |         6 |
|   **-0Z**##### | Count of grouped material qualified Base64 4 char quadlets (context dependent)     | 1,073,741,823 |          8 |         6 |
|   **-0a**##### | Count of anchor seals  (seal groups in list)                                       | 1,073,741,823 |          8 |         6 |


The pound groups `##` or `#####` in the count codes represent variables to be replaced with a Base64 expression of the actual count. Count codes may be stacked to enable concurrent processing. The first code in each stack provides the total quadlet character count for the following group given by the following group count. For example `-Z##-C##` or `-Z##-w##`

The expanded table includes framing codes for full replay of events from a KEL with four forms of attached crypto material in both fully qualified Base64,  `qb64`, and via composition the equivalent fully qualified base2, `qb2`. This will enable all forms of  attached crypto material to be provided in the more compact `qb2` form by merely converting the stream as a whole from Base64 to binary. These are:

1) Indexed controller signatures (existing)  
2) Indexed witness signatures (new)  
3) Nontransferable identifier receipt couplets (new)  
4) Transferable identifier receipt quarlets (new)  
5) Composable groups of groups or primitives (new)
6) Composable groups or primitives in a messages, not JSON, CBOR, or MGPK (new)  
7) Byte/Character counts of composable groups for pipelining and concurrent stream processing (new)  
8) Composed primitives of attached characters that include the count code. Ie a generic primitive whose role is determined solely from context. (new)



### Crypto Material Codes

Existing crypto material codes and indexed signature code tables are defined elsewhere.

ToDo:    
- Simplified parsing algorithm based on new combined Base64 table for converting qb64 primitives to raw (code, raw material).  
- Direct parsing algorithm based on new combined Base2 table for converting qb2 primitives to raw (code, raw material).  
- Define native composable Base64 encoding of messages using composition operators and composable elements
- 

## Why Composability?


### Text Domain Streaming Protocols

A text domain streaming protocol that is also composable as a stream in the binary domain is a novel approach and as a result is largely unfamiliar to developers coming up to speed on KERI. Its primary feature is that the stream may be used, viewed, read, interpreted, processed in the text domain while enabling convenient lossless compression via wholesale conversion as a stream to/from the binary domain. A text domain streaming protocol may be conveniently tunneled or interleaved or annotated within some other text domain representation and then extracted back into a compact form without loss. Most developer's exposure to streaming protocols is exclusively in the binary domain. And with rare exception, binary domain streaming protocols are not not composable (round tripable) to a text domain streaming representation at the stream level.  Thus KERI's approach may even feel somewhat odd. Some historical background and anticipated use case examples might help with better understanding the motivation for and importance of such a feature.  

The early days of computing were governed by extremely limited resources (both computing and bandwidth) that mandated extremely efficient binary protocols. But these came at a cost. They are painful to maintain, debug, parse etc. And binary streaming protocols are the most painful of all.

  
An inflection point in protocol design happened with the advent of JSON. Instead of crafting relatively inflexible binary data structures as the core conveyances in a protoco, JSON enabled flexible self-describing data structures expressed the the human readable text domain. This made protocols defined in JSON not merely human readable, but text parseable, pretty printable, yet still machine interpretable.  Whole families of protocols based on JSON were developed whose major motivation was the native text domain representation. It was certainly not because they were more efficient in any sense of the word for machine processing, transmission, or storage etc. JSON based protocols suffer greatly in terms of efficiency.  In general, once a protocol stack has been developed and hardened, one could argue there was little reason for a human to ever look at the JSON representation itself. Tooling could expose the packets in a human friendly way obviating the need for a native text representation.  But that argument did not win. Computing power had risen enough that the efficiency argument was not decisive. Text representation won instead because the cost of developing the protocol in the first place and making it easy for developers to come up to speed wins adoption battles over binary non-text based protocols. 

  
But we never had the JSON equivalent of a text representation for streaming protocols. JSON is block delimited and enveloped so it is inherently incompatible with streaming protocols. Streaming protocols want to have prepended framing delimiters that allow open ended non-enveloped additive asynchronous transmission of information. But with one exception the core internet streaming protocols are binary. Because well binary is more efficient. But for the same reasons that in spite of its relative gross inefficiency, text domain representation of block delimited data structures (JSON) revolutionized protocol development for non-streaming protocols, we believe that a composable text domain streaming protocol may revolutionize streaming protocol development.  The key feature is that if a stream in text is composable then one may have the considerable advantages of a native text domain representation while enabling convenient lossless conversion at the stream level to a more efficient binary representation. The best of both domains as it were. The composiblity property means that one may convert the text stream to/from a binary stream en mass. It’s a cheap lossless data compression/decompression feature.  

  
Analogously one reason MsgPack and now CBOR have been gaining adoption is that they provide 20-30% compression over JSON but are easily converted to and from JSON. So although they are not human readable they are composable with JSON. One can round trip with no loss between the formats. So processing back ends that benefit from this 30% data compression advantage may seamlessly switch back and forth between MsgPack or CBOR and JSON. They realize the compression efficiency of the binary domain representation while retaining composability to/from the native text domain representation.

 
As mentioned above there is one exception to the fact that legacy streaming protocols are native binary domain only. This exception is a family of native text domain streaming protocols of which the SysLog protocol, IETF RFC-5424 [[22]][[23]], is the prime example. This family includes other text domain, monitoring, audit compliance and computer security based logging protocols [[24]].  These typically use human readable/printable line (white space) delimited streams of structured machine interpretable parsable text. One can convert or compress a Syslog stream into a binary format stream. However, human readability is paramount, therefore the native domain for Syslog is text. The core feature of Syslog like protocols is that they enable the asynchronous streaming of events related to system operation. The set of events is open ended. One may take a snap-shot of the events but inherently the data is best represented, transmitted and stored as an append only event log. Text based streaming protocols, like Syslog, however have very limited composability with binary, usually nothing higher than at a line by line basis so do not benefit from full composability. 

There are obviously similarities between Syslogs and KERI because of the append only event log. This motivates revisiting text streaming protocol design in general, especially with the view of more completely realizing the benefits of total composabilty with an equivalent binary streaming representation.  

But unlike Syslogs which are by-in-large insecure, KERI is a security first protocol. KERI's content is largely cryptographic material and of that digital signatures are by far the most prevalent type. Although less prevalent, public keys, digests and self-certifying identifiers derived from public keys are also vitally important crypto material types in KERI. As described above the most appropriate representation of cryptographic material in the text domain is Base64 with a stable prepended Base64 derivation code.  Protocols in the identity world are by-in-large expressed in the text domain using JSON. These protocols include raw cryptographic material in JSON friendly form usually with either Base64 or Base58. However as discussed above, JSON is incompatible with streaming. Although, embedding JSON within some other streaming protocol that manages the framing of the embedded JSON is possible it is not optimal. JSON is fundamentally a close ended data envelope. At a very fundamental level this is a representation scheme that is diametrically incoherent with the open ended streaming of asynchronous events. We need something better. That something better is a native text domain streaming protocol that supports the conveyance of cryptographic information in a secure manner and is composable to the binary domain to gain transmission efficiency when needed.  The former sentence succinctly expresses the primary goals of KERI's streaming protocol design. This makes composability between the native text and compact binary domains an essential feature. 

### Auditable Secure Text Streams  

The seminal use case for KERI's secure text streaming protocol may be a family of use cases that combine security, legal, and archival requirements. This family include legally binding electronically signed documents and document streams, compliance logs, and audit trails. These all may be very important adoption vectors for KERI. Of the three requirements, security, legal, and archival, let's first start with the latter and work backwards. 

#### Preservation

The ISO ISO 14641:2018 standard for the preservation of electronic documents, lists four important features of a legally defensible archive [[33]][[34]]. These are long-term preservation, data integrity, data security, and traceability. A KERI Key Event Receipt Log (KERL) is already in a form that provides, to a large extent, data integrity, data security, and traceability. All that is needed is to ensure long-term preservation capability. The standard formats for long-term document archival are by-in-large text based (with some exceptions) [[30]]. With PDF/A being the primary preferred format and ASCII text as the secondary preferred format [[30]]. PDF/A (ISO-19005-1) is the archival version of PDF with some restrictions to constrain the inclusion of various types of non-textual information [[32]].  PDF is based on PostScript, a text language [[31]]. PDf can be entirely represented using characters from the visible printable ASCII characters set [[31]]. PDF/A guarantees that the document text is extractable and that the logical structure and content of the integrated text material remain intact [[32]]. What this means is that a KERI event log stream in a native text format is inherently compatible with archival requirements. Indeed because a KERL text stream with composition operators only uses the Base64URL character set, that is, 
```regex
[A-Z,a-z,0-9,-,_]
```
then any of the other characters in the ASCII set may be used to losslessly annotate a KERI text event stream. These include white space characters. Primitives and groups of framed primitives within the text KERL could then be line delimited and white spaced and comments added using the "#" symbol for example. A text parser could easily strip all non Base-64 characters, line delimiters and comments to reconstitute the KERL stream which could then be converted en mass for transmission. The archivist never need access or convert to the raw binary format. In other words the archivist may always stay in either the T or S domains and never need convert to the R domain. 

There is one complication. Although KERI attachments have an ASCII text compliant representation, KERI message data may not. Serialized KERI message data may be in either JSON, CBOR or MsgPack. The former, JSON, is ASCII text but the latter two are not ASCII text. However the non ASCII bytes in CBOR or MsgPack serializations may be expressed using a more verbose (compared to Base64) escaped text representation. This requires breaking any KERL stream into streamlets at message boundaries. To clarify, a streamlet is a message followed by attachments. As mentioned above, however, a work item is to define a composable Base64 representation for KERI messages. When messages are represented in composable Base64 then a KERL stream would not have to be broken into streamlets at message boundaries.   

A text domain KERL could be tunneled via a Syslog. Syslog events may include structured data. Syslog compliant structured data must be 7-bit ASCII text [[22]]. A Syslog with embedded KERL events and attachments could be considered an annotated KERL. Similarly, a PDF/A document with embedded KERL may be described as an annotated text format.

To restate, with a text domain streaming representation for a KERL, a legally defensible archive that includes KERLs never need to ever access the raw binary, (dc, rm) for archival purposes but benefits from conversion to streaming binary, qb2, for streaming to/from the archival format, qb64.

#### Legal Digital Signatures

KERI's main purpose is to securely establish control authority over a self-certifying identifier. Control authority is held by the entity that controls the associated private keys belonging to a set of asymmetric (public, private) key pairs. Establishment of control authority is provided by cryptographically verifiable proof of key state, that is, a proof that a given set of key pairs are the authoritative ones. This proof is expressed as a KERI KERL (Key Event Receipt Log) which is a hash chained signed data structure.  In KERI parlance, the holder of the authoritative private keys is the *controller* of the associated identifier.

When a set of legally defined conditions are met, a cryptographic digital signature based on asymmetric key pairs like the ones KERI uses has legal standing. In other words the key pairs used to control a KERI self-certifying identifier may also be used to create legally binding electronic signatures on electronic documents.

The most relevant condition (to KERI) that a legally binding signature must satisfy is proof or assurance that the entity creating the electronic signature is also the entity that is the controller of the associated private keys. A KERI KERL may be used to support that proof or assurance. An annoted text domain KERL could be attached to the signed legal document as an appendix or provided to an electronic signature notary. This text based annotated KERL appendix could be archived with all the associated legal documents. This greatly facilitate the broader adoption of electronic signatures and KERI. This could also help reduce trust transaction costs for the authentic data economy.

The relevant legislation for legally compliant electronic signatures are the USA Electronic Signatures in Global and National Commerce Act (ESIGN), the USA Uniform Eletronic Transactions Act (UETA) and the
EU Regulation for Electronic Identification and Electronic Trust Services (eIDAS) [[27]][[28]][[29]]. The legislation have similar conditions at least those relevant to KERI. But as an illustrative example let's consider eIDAS.


> Legal effects of eSignatures.
> 
> An advanced eSignature based on a qualified certificate satisfies the legal requirements of a signature in relation to data in electronic form in the same way as a handwritten signature satisfies those requirements in relation to paper-based data. For convenience, this type of signature can be called a ‘qualified eSignature’.  It is also admissible as evidence in legal proceedings. An advanced electronic signature, meets the following requirements: it is uniquely linked to the signatory; it is capable of identifying the signatory; it is created using means that signatories can maintain under their sole control; it is linked to the electronic document to be authenticated. This is to ensure that any subsequent change in that document is detectable.

The unique signatory identification and sole control conditions are closely aligned with KERI's inherent capability to provide proof of control authority over an identifier via a KERL.

> Liability of qualified eSignatures.
> 
> EU countries must ensure that a certification-service provider which issues a qualified certificate takes certain responsibilities. These include liability for damages in regard to any person or entity who reasonably relies on the certificate for: the accuracy of all information in the qualified certificate at the time of its issue, the fact that the certificate contains all the details prescribed for a qualified certificate at the time of its issue, and that the signatory identified in the certificate is the person to whom it was issued.

A certification-service provider is a type of notary. A certification service provider may be considered as a special type of judge in the KERI parlance. A W3C verifiable credential (VC) issued by a KERI identified issuer (notary) and to a KERI identified issuee (signatory), that certifies a signature by the signatory on a document may be a prime use case for KERI. It would appear that a KERI signatory plus an appropriate notarizing VC may qualify as a legal signature under this legislation. In such a case, text domain archivable KERLs could be attached to provide proof of control over the associated identifiers and key pairs not only of the signatory, but the notary, the certificate, and the signed document itself. KERI's features have the potential to make e-signing universal for all transactions.

Recall that in KERI, the controller of an identifier via its authoritative controlling key pairs is solely responsible for event creation and ordering and commits to that via non-repudiable digital signatures on the events. This is compatible with the legal requirement for sole-control. A shared distributed ledger, on the other hand, may not impose equivalent liability because the controller using a ledger is not solely responsible for event creation and event ordering and may not therefore similarly establish sole-control. Access to the shared ledger is via some other set of key-pairs not those controlling the identifier. Thus lack of proof of sole control over the private keys for identifiers established on a shared ledger may invalidate the legal status for liability under the legislation.

#### Audit Trails

In general data integrity with non-repudiation is an important requirement in compliance audits. A simpler way of describing that requirement is provenance. An audit log is used to provenance something. An annotated text domain KERL could be used to support a securely attributed tamper evident archival audit trail [[24]][[25]][[26]]. Composability would allow archival in streaming text form while also enabling rapid transmission en mass in streaming binary form.


For example the Electronic Code of Federal Regulations: Electronic Signatures (E-CFR) regulation requires audit trails on electronic data including nonredudiable attribution via digital signatures. Relevant clauses are provided below as follows [[25]]:

> E-CFR
> 
> (e) Use of secure, computer-generated, time-stamped audit trails to independently record the date and time of operator entries and actions that create, modify, or delete electronic records. Record changes shall not obscure previously recorded information. Such audit trail documentation shall be retained for a period at least as long as that required for the subject electronic records and shall be available for agency review and copying.
> 
> (f) Use of operational system checks to enforce permitted sequencing of steps and events, as appropriate.
> 
> (g) Use of authority checks to ensure that only authorized individuals can use the system, electronically sign a record, access the operation or computer system input or output device, alter a record, or perform the operation at hand.
> 
> (j) The establishment of, and adherence to, written policies that hold individuals accountable and responsible for actions initiated under their electronic signatures, in order to deter record and signature falsification.

The Alliance for Telecommunications Industry Solutions (ATIS ) provides various definitions for audit trail as follows [[26]]:

> A record of both completed and attempted accesses and service. Data in the form of a logical path linking a sequence of events, used to trace the transactions that have affected the contents of a record. Chronological record of system activities to enable the reconstruction and examination of the sequence of events and/or changes in an event.  The set of records generated by a system in response to accounting operations, providing the basis for audit. A set of records that collectively provide documentary evidence of processing used to aid in tracing from original transactions forward to related records and reports, and/or backwards from records and reports to their component source transactions.

KERI supports secure attribution via non-repudiable signatures on any data in such a compliance log. The proof of control authority over such signatures is provided via a KERL. The key events in the KERL may be interspersed in the audit trail so that the timing of key events that rotate keys may be correlated to the audit log signed data. The audit trail may be viewed as an annotated KERL. Moreover, if the auditable data is anchored to the KERL itself, then that anchored data may be interspersed with the associated KEY events that establish control over the signatures on the auditable data itself. A text processor could extract the KERL from any archived audit trail and then convert it to streaming binary for compact transmission to a processor to perform the cryptographic verification operations. This provides efficient scalable provenance.


### Summary

The foregoing examples illustrate why one might consider composability of KERLs between the streaming text and streaming binary domains an essential feature of KERI that better enables the authentic data economy.



## References


[1]. Smith, S. M., "Key Event Receipt Infrastructure (KERI) Design"  

[1]: https://github.com/SmithSamuelM/Papers/blob/master/whitepapers/KERI_WP_2.x.web.pdf  

[2]. URI Standard RFC3986  

[2]: https://tools.ietf.org/html/rfc3986  

[3]. Base64URL File Safe Standard RFC 4648  

[3]: https://tools.ietf.org/html/rfc4648  

[4]. “Decentralized Identifiers (DIDs),” W3C Draft Community Group Report 23 August 2018.  

[4]: https://w3c-ccg.github.io/did-spec/  

[5]. Convolution Theorem  

[5]: https://en.wikipedia.org/wiki/Convolution_theorem  

[6].Knee, M.J. & Wells, N.D., "Seamless Concatenation -
A 21st Century Dream  

[6]: http://downloads.bbc.co.uk/rd/pubs/papers/paper_03/paper_03.html

[7]. Lossless Streaming Data Compression.  

[7]: https://en.wikipedia.org/wiki/Lossless_compression  

[8]. UTF-8 Standard  

[8]: https://en.wikipedia.org/wiki/UTF-8  

[9]. ASCII Standard  

[9]: https://en.wikipedia.org/wiki/ASCII  

[10]. IPFS Multihash  

[10]: https://richardschneider.github.io/net-ipfs-core/api/Ipfs.Registry.HashingAlgorithm.html  

[11]. IPFS Multicodec Multihash Hash Algorithm Table  

[11]: https://github.com/multiformats/multicodec/blob/master/table.csv  

[12]. Multicodec   

[12]: https://github.com/multiformats/multicodec/blob/master/README.md  

[13]. did:key method  

[13]: https://w3c-ccg.github.io/did-method-key/  

[14]. did:peer method  

[14]: https://identity.foundation/peer-did-method-spec/  

[15]. Base58 Check

[15]: https://en.bitcoin.it/wiki/Base58Check_encoding#Base58_symbol_chart  

[16]. JSON Mapping Object Delimeters  

[16]: https://www.json.org/json-en.html  

[17]. CBOR Mapping Object Codes  

[17]: https://en.wikipedia.org/wiki/CBOR  

[18]. MsgPack Mapping Object Codes  

[18]: https://github.com/msgpack/msgpack/blob/master/spec.md  

[19]. UTF Byte Order Mark (BOM)  

[19]: https://en.wikipedia.org/wiki/Byte_order_mark  

[20]. Crypto Construct Language (CCLang)  

[20]: https://github.com/dhuseby/cclang  

[21]: Bitcoin pay-to-script-hash  

[21]: https://en.bitcoin.it/wiki/Pay_to_script_hash  

[22]. IETF Syslog Protocol RFC-5424   

[22]: https://www.rfc-editor.org/rfc/rfc5424.txt  

[23]. Syslog Tutorial  

[23]: https://stackify.com/syslog-101/  

[24]. Audit Trail

[24]: https://en.wikipedia.org/wiki/Audit_trail

[25]. E-CFR Electronic Code of Federal Regulations: Electronic Signatures

[25]: https://web.archive.org/web/20100608090316/http://ecfr.gpoaccess.gov/cgi/t/text/text-idx?c=ecfr&sid=3094bb76639c37239557767756fd7878&rgn=div5&view=text&node=21%3A1.0.1.1.7&idno=21

[26]. ATIS Alliance for Telecommunications Industry Solutions: Audit Trail  

[26]: https://web.archive.org/web/20130313232104/http://www.atis.org/glossary/definition.aspx?id=5572  

[27]. Electronic Signatures and the Law.

[27]: https://en.wikipedia.org/wiki/Electronic_signatures_and_law

[28]. Legality of Electronic Signatures.  

[28]. https://acrobat.adobe.com/us/en/sign/compliance/electronic-signature-legality.html  

[29]. Legal Guide to Electronic Signatures.

[29]: https://www.adobe.com/content/dam/dx-dc/pdf/ue/adobe-sign-us-guide-e-signatures-wp-ue.pdf

[30]. Smithsonian Preservation Formats  

[30]: https://siarchives.si.edu/what-we-do/digital-curation/recommended-preservation-formats-electronic-records  

[31]. PDF Document Format  

[31]. https://www.adobe.com/content/dam/acom/en/devnet/pdf/pdfs/pdf_reference_archives/PDFReference.pdf  

[32]. PDF/A ISO-19005-1 The Standard for Long-term Archiving  

[32]: https://www.pdfa.org/wp-content/until2016_uploads/2011/08/PDFA_The-Basics_A-new-standard-for-long-term-archiving.pdf  

[33]. Legally Defensible Archiving  

[33]: https://www.netgovern.com/blog-post/compliance/four-key-requirements-legally-defensible-archive  

[34]. ISO 14641:2018  Design and operation of an information system for the preservation of electronic documents.  

[34]: https://www.iso.org/standard/74338.html  

[35]. IETF Collective Edwards-Curve Digital Signature Algorithm Draft  Proposal

[35]: https://tools.ietf.org/id/draft-ford-cfrg-cosi-00.html

[36]. "Boneh, Dan; Boyen, Xavier; and Shacham, Hovav "Short Group Signatures" (BBS Signatures)

[36]: http://ai.stanford.edu/~xb/crypto04a/groupsigs.pdf

[37]. Camenisch, Jan; Drijvers, Manu; and Lehmann, Anja ; "Anonymous Attestation Using the Strong Diffie Hellman Assumption Revisited"  

[37]: https://eprint.iacr.org/2016/663.pdf

