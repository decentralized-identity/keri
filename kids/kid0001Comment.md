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

One of the most important design goals for KERI is performance in data streaming applications. This goal exhibits itself in many design choices throughout the KERI implementation. This includes asynchronous operation, support for bare metal protocols like TCP and UDP, streaming friendly evelopeless signature and receipt attachments and compact encoding of both events and cryptographic material. This document addresses specifically the compact cryptographic material encoding schemes and how they support higher performance asynchronous streaming of KERI events and attachments. 

### Asynchronous Replay of Attached Cryptographic Material

KERI is based on cryptographic proofs of control authority via verifiable hash chained signed data structures called Key Event Logs. Because almost every decision made a component of KERI requires access to one or more KELs, compact encoding of those KELs may provide significant performance benefits. But an even more compelling reason for compact encoding of cryptographic material is not just the events themselves the attached signatures and receipts to those events. The vast majority of bandwidth consumed in communications between KERI components such as controllers, validators, witnesses, watchers, jurors, and judges will be due attached signatures and receipts. These may dwarf the associated events by two orders of magnitude. This is especially true when replaying Key Event Logs (KELs) between any two components.

For example most of the cryptographic material inside an event consists of public keys, digests and identifiers. Identifiers are usually expressed as a public key or a digest. The minimum security level for KERI is 128 bits of cryptographic strength. For ECC (public, private) key-pairs, such as, Ed25519 or EcDSA secp256k1 these means 32 byte (256 bit) and 33 byte long public keys respectively. Likewise cryptographic digests (hashes) with 128 bits of cryptographic strength and post quantum resistance, such as, Blake3 or Sha3 this means 32 byte (256 bit) long digests. On the other hand the signatures for Ed25519 and EcDSA secp256k1 are 64 byte (512 bit) long. In normal operation where events are being disseminated the receipts are exchanged asynchronously in part (not all at once). But replay or cloning of a KEL will involve full streaming of all the events and attached signatures and receipts. 

Suppose an identifier uses a 3 of 5 multi-sig scheme. Each event could have up to 5 attached signatures. A public identifier could also have witnesses. Suppose the number of witnesses is 10. Thus a replay of any event could include all 10 of the the witness receipts (signatures). Finally the watcher network for any given validator may have many more watchers than witnesses and each watcher may sign their copy of the event and gossip it to the other watchers. Suppose there are 100 watchers that a validator trusts, a replay of the event log of that validator with all the watcher receipts (signatures) could include 100 watcher signatures for each event. Moreover, the attached signatures need to be identified so that they may be matched with the proper public keys. For signatures of the controller the public keys are in an ordered list so the signatures could be matched to the public key using an index into the ordered list. Likewise for witnesses in an ordered witness list. However in general for watchers (and witnesses) that use non-transferable identifiers the public key may be found in the associated identifier so a given witness/watcher signature can be matched with its public key merely by attaching the witness/watcher identifier.  Validators and other components such as jurors and judgers may use transferable identifiers each with a multi-sig set of public keys. Thus attached signatures will need additional information such as a location seal into the KEL of the validator with transferable identifier in order to get the public keys.  Thus the bandwidth requirements of the replay of a given KEL with multiple identifiers may be dominated by the attached signatures and associated identitifiers by at least two orders of magnitude more  than the events.  Indeed because of the differences how the public keys for the signatures may be identified the attached receipt signatures are not composed as a homogenous group but may have at least 3 or more different types of groups of sigantures with different additional cryptographic material besides the signatures. 

### Composable Concatenation of Heterogenous Attachments

KERI's design goal is to provide these signatures (receipts) in a compact concatenation composable manner that is compatible with asynchronous streaming on bare metal protocols. This makes enveloping, where some set of block delimeters are used to enveloge each set of attachments, a poor choice. Delimited enveloping schemes are verbose and require sychronizing the assemblage of the full enveloped attached material prior to transmission of any material. Whereas concatenated attachments may begin streaming asynchronously before all have been assembled. And heterogeneous attachment groups benefit from framing or grouping composition operators such as counters or other inserted attachments. 

Streaming concatenated attachments is analogous to streaming frames in many data streaming protocols such as video and audio stream protocols. Especially protocols for lossless compression algorithms [[6]][[7]]. Heterogenous composed attachments are analogous to different types of frames in these protocols and inserted grouping compostion operaters are analogous to framing headers. These are also called bitstrea splicing operators [[7]]. Therefore efficient asynchronous replay of the attached concatenated cryptographic material for signatures and receipts is an important design constraint for KERI. This constitues an important domain of operation for the cryptographic material in KERI.

## Cryptographic Material Encoding

Cryptographic operations require large random or pseudo random numbers. The typical representation used by cryptographic libraries is not actually number in the strict computer sense but is an array or string of bytes. In Python for example, crypto libraries input and output cryptographic material as bytes (byte string) objects. Different types of cryptographic material are distinquished by the type of cryptographic material and the crypto suite that the material is a part of with associated operations from a crypto suite specific library. The typical approach is to house the raw material together with the type and crypto suite (version) in a data structure. For example, Ed25519, is a crypto suite for digital signatures with cryptographic material types that are private keys, public keys and signatures. The associated operations are key pair creation, signing, and signature verification. The internal storage and processing of the data structure fields is usually not a limiting concern. Its only when transmitting over the wire where bandwidth constraints demand more compact representations.

### Raw Binary Material with Code

Some serializations of data structures are relatively verbose. JSON is a prime example.  High performance data streaming applications such as those that KERI intends to support would suffer greatly from such verbose serializations like JSON especially given the volume of attached signatures and receipts contemplated for KERI. There are other more compact serializations for data structures such as CBOR or MSGPack but any data structure serialization is still relatively verbose. The over the wire serialization and representation of each cryptogrpahic material item would benefit from a much more compact representation than a serialized data structure. One way to manage this is to use context to remove many of the fields in the data structure. That is the context may be used to determine how the cryptographic material is derived. Any remaining derivation information may then be compactly encoded into an indexed table.  The index may then serve as a derivation code for the cryptographic material. Each derivation code in the table may be used to represent some unique combination of derivation information that together with the context of where the code is used determine unambiguously the nature of the associated cryptographic material. Thus using context together with a derivation code table we may obtain the most compact representation practically possible. There are only a few highly performant cryptographic suites and only a few types of material for each suite. Leveraging this allows KERI to use a compact derivation code from a relatively small table, where each entry in the table combines all the essential fields from a much more verbose crypto material data structure into one code. One can always define a mapping that explodes the derivation code table into more verbose representations such as JSON Web Tokens or other similar encodings. The result is that each crypto material item may be represented by two fields, these are, the derivation code and the raw material. The derivation code may then be prefixed to the raw material to create the most compact seralization form possible. We can abstractly represent each cryptographic material item with a two element representation expressed as a tuple as follows:

*(dc, rm)*

 where *dc* represents the derivation code and *rm* represents the raw material.


### Namespace Compatibililty of Identifier Prefixes and Other Cryptographic Material


KERI is an identifier system that is meant to provide secure control over namespaces. The most widely used namespace is the URI standard which includes URNs and URLs [[2]]. URI namespaces are represented using a textual encoding. This makes it easy for human meaningful interaction and use of the name space. Humans primarily interface to computing system via text. A textual representation has the highest potential for broad or universal adoption. ASCII is the most widely adopted and supported textual representation and URIs by-in-large use ASCII compatible text representations. The more modern UTF-8 text standard has the desirable feature that non-control ASCII text (and many control characters) are identically represented in UTF-8. For similar reasons, many other important namespace standards such as file systems also use an ASCII/UTF-8 textual representation. Consequently for KERI to attain broad adoption as an identfier system, its identifiers would greatly benefit from a native textual representation.

The difficulty is that KERI's self certifying identifier prefixes are derived cryptographic material, that is, long strings of pseudo random bytes. Thus to express these identifiers in a text based namespace such as a URI, file system, or others we need a textual representation or encoding of the associated cryptographic material. The most practical compatible textual encoding both due to its almost univerasl support and compactness is a Base64 encoding [[3]]. Base64 maps 6 bits of raw binary data to a single ASCII printable text character. Each ASCII character uses 8 bits of binary data. So Base64 is a less compact representation that is more compatible with human meaningful namespace standards. Although a Base64 expression of a 32 byte binary array of bytes is not very memorable, it is text and can but used as part of a textual namespace such as URL or other textual namespaces such as the W3C DID standard [[4]]. The are two variants of Base64, one is plain or conventional Base64 and the other is Base64-URL for Base64 that is both URL and file safe. Base64-URL is the variant we want for namespace compatibility. 

A futher important consideration if that KERI's security is largely based on cryptographic digital signatures. A signature is only verifiable against a specific serialzation encoding of the signed data. Thus a signature on a raw binary string of bytes will not verify against the Base64 encoded version and vice versa. Signatures attached to data allow one to verify the authenticity of data to the controller of the private keys used to create the signature.  One important use case is for one entity to issue a signed statement to includes a reference to some other entities identifier. Thus the representation of the other identifier in that statement is the only verifiable representation vis a vis that signature. Consequently, the native encoding representation of signature verifiable (authenticatable) statements may be a determining factor in what should be the native encoding or representation for KERI identifiers. Most statements used in human meaningful interactions are represented in a text not a raw binary encoding and the popular text encoding is ASCII or the ASCII compatible UTF-8. Therefore the native representation for KERI identifiers should also be ASCII compatable, and as mentioned above, the most compact practical choice is Base64-URL [[3]]. For the sake of simplicity, herein everywhere Base64 is referenced it is meant the URL file safe variant of Base64 unless otherwise qualified.

Another important property of Base64 is that it may be applied to convert a stream of composed items that and then the stream may be converted back and decomposed without data loss. Other encodings such as Base58 Check are not composable but require each item to be parsed or framed and converted seperately [[15]].

Given that KERI cryptographically derived identifiers are to be expressed in Base64, we must answer the question of how to map the tuple of as derivation code and raw material, *(dc, rm)*, to a single string of Base64 characters. We may extend this same encoding approach to not merely self certifying identifiers but any of the cryptographic material items used in KERI. These include in addition to identifiers, public keys, private keys, digests, signatures and other items.

The choices are:

A) First prepend (concatenate) a derivation code expressed in binary to the cryptographic raw material and then convert the resultant array of binary characters to Base64. (unstable derivation code representation)

B) First convert the raw material to Base64 and then prepend the derivation code expressed in Base64 to the converted raw material. (stable derivation code representation)


We must prepend, not append the derivation code because any parser needs to knows how to interprete the appended raw material and may do this by first extracting and processing the derivation code and then extracting the remaining characters which are the cryptographic material. This is especially important if there are no delimiters or framing headers that separate one cryptographic material item the next. We call this self-framing. Where the derivation code itself serves as an encapsulated framing header for the cryptographic material item. This is a very useful feature in any data streaming protocol for which KERI was designed to support because it provides and extremely efficient if not the most efficient representation possible.

Of the two choices KERI has chosen the latter. This has the property we call stable derivation code representation. The former has conversely an unstable derivation code representation.

To understand why we must understand how Base64 conversion works. Raw binary is represented as a string or array of bytes where each byte is an octet of 8 bits. When converting such a string of bytes to Base64, the string of 8 bit octets is subdivided into a string of 6 bit sextets. Each sextet is then converted to a single Base64 text character. 

Lets then compare what happens if we first prepend a binary derivation code and then convert the concatenated string of bytes. Suppose that the derivation code is only 1 byte. The analysis applies to any length derivation code at least with regards the trailing byte or bytes of longer derivation codes.

For a one byte derivation code the first six bits (1 sextet) map to a single Base64 character but the remaining 2 bits of the derivation code byte are combined with the first 4 bits of the first byte of the cryptographic material to form the second Base64 character. The actual Base64 character changes based on the specific cryptographic material item. This means that the derivation code representation is not stable (hence unstable). This is an undesirable feature for readability in the name space domain. Although long strings of Base64 characters are not very human meaningful, they are still text and much more human meaningful in terms of reading and comparison that a binary representation. More importantly, the derivations codes may be short even as short as one Base64 text character. Such short codes are easily recongizeable and are helpful when reading statements or namespace identifers that include such cryptographic material because the crypto suite and cryptographic material type is thereby easily recognizable which has value when debugging and interpreting statements that include the Base64 representation of the identifiers. Thus if we want stability of the derivation code representation in the text domain means we want to use the second approach for mapping the *(dc, rm)*  representtion to and from the Base64 text representation. There is one case where it doesn't matter, i.e. we get stability with either approach. The least common multiple of 6 bits and 8 bits is 24 bits or 3 bytes. Any byte string that is a multiple of 3 bytes will convert to an integral multiple of 4 base64 text characters. Consequently if the derivation code in binary were constrained to always be a multiple of 3 bytes then its corresponding Base64 representation would always be a multiple of 4 Base64 characters and therefor be stable. It would not include any bits from the appended cryptographic material. However, constraining the derivation code to be a multiple of 3 bytes (4 Base64 characters) means that we can not use more compact 1 char or 2 character derivation codes. But using the second approach for the mapping allows us to both have a stable representation and use shorter derivation codes.

Furthermore the non-integral mixing (unstable representation) of the trailing byte of the derivation code with the first byte of the cryptographic material means that text based parsers may not extract the derivation code as an integral number of Base64 charcters and then likewise extract the remaining cryptographic material as an integral number of Base64 characters. A parser must use a combination of text and binary operations (bit shifts) to extract the cryptographic material. Or must first convert the combined element to binary before parsing. This may be cumbersome for text based parsers. 

To conclude, stability and integral representation in the text domain indicates that the preferred approach (as selected by KERI) for mapping between the *(dc, rm)* representation and the Base64 represention is to first convert the *rm* into Base64 and then prepend an integral number of Base64 characters as the base64 derivation code. The representation of the derivation code in the *(dc, cm)* tuple could either be the base64 characters or the equivalent binary representation but in the later case then the binary *dc* would also be converted to and integral number of Base64 characters before being prepended to the Base64 *rm* characters.

We can formally label this mapping as *R2T* for *Raw* binary tuple to Base64 *Text* and *T2R* for Base64 *Text* to *Raw* binary tuple.



### Streaming Binary

The final consideration is how to decide on the exact Base 64 derivation codes including code lengths as well as future extensibility. What other properties of the derivation codes might be useful or valuable? One obvious consideration is the streaming efficiency. Base64 is not as compact as binary. There is a 33% size penalty when streaming a Base64 representation of a data stream comparared to the binary representation of the same stream. Base64 is 4/3 bigger than the binary or 1/3 larger. As detailed above, the volume and heterogenous nature of KERI cryptographic material attachments (siganture, receipts, etc) makes removing that 33% performance penalty by defining a binary streaming representation of the associated cryptographic material very attractive.

One approach for a more compact binary streaming representaion is to create a hybrid representation where the Base64 derivation code is followed by, not the Base64 version of the cryptographic material, but by the raw binary version. This majorly captures the size advantage. However a parser has no way of telling if the remaining bytes of a given cryptographic material item are in Base64 or in binary merely from the prepended derivation code. There are three ways to solve this problem.

1) Have unique derivation code for each variant Base64 and binary crypto material. But this effectively doubles the size of the derivation code table. This may become problematic over time and may contribute to a relaively inefficient code. 

2) Use context of where a given crypto material item appears to indicate how to parse the format of the attached crypto material (Base64 or binary). This has the disadvantage that there may not be enough contextual information in the attached crypto material stream to always unambiguously determine the variant. This would make it difficult to generally take advantage of the size benefits of the more compact binary version.

3) Use an additional prepended composition or context framing code to indicate that following cryptographic material item is using binary for its raw material element. This is more verbose but does not require expanding the table and if the prepended framing code may be applied to a contiguous group of similarly composed cryptographic material items then the increased size may be amortized across multiple items for each framing code. These approach seems to provide a beneficial compromise between the former two other approaches.

The preferred approach is that later one, that is, use additional framing codes to allow composition of groups of cryptographic material that may depending on the framing code use Base64 or binary represeantations. This allows composition of heterogenous cryptographic groups that may use the more verbose Base64 or the more compact binary representations for streaming attached material over the wire. 

#### Composition Property

There is however one remaining complexity in choosing the composition approach, that is how flexible and extensible or conversly how rigid and limited are the compositions. Clearly prepending a framing code to each cryptographic material item merely to indicate binary or Base64 is not very attractive. It makes more sense to prepend a framing code to a group of items. The complexity is that a transformation of a group of crypto material items formed by concatenation in either the Base64 domain or the binary domain does not necessarily preserve the integrity at the byte level of each individual crypto item when the group of items is converted as a group. So framed groups cannot be parsed individually. Indeed we reencounter the same problem described above, where bits from trailing byte of one member of the group may become mixed with bits from the leading byte of the next member of the group unless each member is seperately converted but not as a group. This is because of misalignment of 6 bit sextet segmentation in Base64 character streams and the 8 bit octent segmentation in binary byte streams.


In streaming protocols the ability to flexibly compose frames of items that respect byte boundaries and to inject other frames or recompose frames into sub frames enables flexibilty and extensiblity. Without this flexibility it becomes more difficult at the streaming level when one wants to compress streams. This flexible composition allows for in stream recomposition that is analogous to operations employed in bitstream splicing and lossless streaming data compression [[6]][[7]]. Flexibly composiblity is also helpful in load balancing, routing, and quality of service stream processing. Another analogy is to convolution theorem from signal processing. The convolution theorem states that convolution in time domain corresponds to multiplication in frequency domain and vice versa [[5]]. Multiplication and convolution are two different composition and decompostion operations that enable powerful efficient signal processing algorithms.
In this case, we have a much simpler composition and decompostion operations, these are concatenation and its inverse de-concatenation to both the text (Base64) and binary domains. 

To better formalize the discussion, let the term *primitive* refer to an atomic element that that may be composed/decomposed via concatenation in a stream. Conversion of any composition via concatenation of any set of *primitives* in a stream between one domain and the other must always respect *primitive* boundaries at the byte level after the conversion. This means 8 bit binary octets in binary, and 8 bit Base64 characters that represent 6 bit sextets in text. Flexible parsing of concatenation compositions benefit from preserving byte or character boundaries of each *primitive* when converting streams between each domain, text and binary.

Lets label the streaming binary representation *S* and the streaming Base64 representation *T*. Then we have two mappings *S2T* and *T2S*. Or more compactly *S* for *T2S* and *T* for *S2T*. We can also symbolize the two different representations with a superscript *s* for streaming binary and  *t* for streaming Base64 text on a variable, say *x* that in turn represents a given primitive as follows:


<a href="https://www.codecogs.com/eqnedit.php?latex=x_{}^{t}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?x_{}^{t}" title="x_{}^{t}" /></a>

and

<a href="https://www.codecogs.com/eqnedit.php?latex=x_{}^{s}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?x_{}^{s}" title="x_{}^{s}" /></a>.

And transformation between the *T* and *S* domains may be represented as follows:



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


Now given the binary is composed of bytes each representing 8 bits (octet) and Base64 is composed of ASCII text characters of size 8 bits but representing 6 bits (sextet) then to concatenation composition property is satisfied if any primitive in binary has a length that is an integer multiple of 3 bytes and any primitive in Base64 has a length that is an integer multiple of 4 Base64 text characters. This is because 24  bits is the least common multiple of 8 bits and 6 bits respecively. And 24 bits is represented by 3 binary bytes or 4 Base64 characters. Any primitive must align on 24 bit boundaries. Otherwise some bits from the preceding primitive's trailing byte become mingled with bits from the succeding primitive's leading byte. A parser then cannot cleanly segment one primitive from the next along byte or character boundaries but must process both together. This may be extremely cumbersome and as a result entirely problematic in high performance streaming applications of KERI.

#### Direct Primitive Conversion to Binary from Stable Code Textual

Let's consider what happens when we directly convert a text based primitive to streaming binary where the derivation code is expressed as an integral number of Base64 characters and is prepended to the Base64 conversion of the raw binary crypto material. In other words we are mapping from *R* to *T* to *S*. In *R* we have a tuple *(dc, rm)*. In T a Base64 character string where the first character or characters are the derivaion code, *dc*, and the remaining characters are the Base64 conversion of *rm*. In *S* a binary byte string where the first sextet or sextet (6 bit) are the binary equivalents of the Base64 *dc* and the remaining sextets are the binary equivalents of the Base64 crypto material *cm*.  The mapping path looks like this,

*(dc, rm)* to *T* to *S*.

This is the approach as described above that results in stable derivation code characters in the textual domain. Lets further also suppose that the combined primitive, derivation code plus appended crypto material, all in Base64, satisfies the composibilty property. This means that the combination, i.e. the primitive has a length that is an integer multiple of 4 (Base64 characters). So we satisfy both code stability and composibility.

The Base64 standard implementation appends pad characters to any conversion from binary to Base64 to ensure that the length of the converted primitive is a multiple of 4 Base64 chars. In other words a standard Base64 conversion is designed to provide composability in the Basee64 domain. Many uses of Base64 do not benefit from composability and in those applications the pad characters may be removed. If the application can ensure that the converted primitive will always appear in a framed or delimited manner such that a concatenated group of successive primitives would never be converted back to binary as a group, then one may ignore the pad characters. But in the case of KERI where we see a benefit from composiblity, we can prepend derivation codes that ensure primitives are composable without using pad characters by ensuring that the combination of derivation code plus appended crypto material has a length that is an integer multiple of 4 Base64 characters. 

Any crypto material in bytes that is not an integer multiple of 3 bytes will convert to Base64 with either 1 or 2 pad characters but never 3. This is because division by three may leave 1, 2, or 0 as a remainder. A remainder of 1 octet (8 bits) requires two sextets (2 * 6 = 12 bits) to fully encode it. The remaining 4 bits in the 2 sextets are pad bits (not bytes or characters). But 2 sextets is not an integer multiple of 4 so two additional pad characters are required to get to 4. Thus one byte encodes to 4 Base64 characaters of which 2 are pad characters. A remainder of 2 octets (2 * 8 = 16 bits) requires 3 sextets  (3 * 6 = 18 bits) to fully encode it. One additional pad character is required to get to 4 characters total. Thus in a binary to base64 conversion that preserves composability there may be 0, 1, or 2 pad bytes. Coresponding respectively to a reminder of 0, 2 or 1 bytes when the number of bytes is divided by 3.


Recall that a derivation code that is an integral multiple of 4 Base64 characters will map to an integral multiple of 3 binary bytes. That is the uninteresting case. The interesting case is a derivation code that is not an integrer multiple of 4 Base64 characters. The simplest case is a derivation code that is one Base64 character. This is useful if the crypto material converts to Base64 with one pad character because the pad character can be stripped off and the code prepended to make the length of the combination an integral multiple of 4 Base64 characters which will in turn convert to an integer multiple of 3 bytes. 

The simplest case looks like this. We start with dc = 1 Base 54 character and rm = 2 bytes. The raw material rm converts to 4 Base64 characters including 1 pad character. Removing the pad character and prepending the dc gives a textual representaion with 4 Base64 characters. The minimum size possible that also satisfies the composiblity property.

Converting the combined primitive as a whole to binary from Base64 results in 3 binary bytes, also the minimum size possible that also satisfies the composiblity property. The layout in bits of this converted form is as follows:

6 bits provide the binary version of the dc, 16 bits are the raw binary, 2 bits of padding. The act of prepending a dc character effectively shifted the raw binary to the left by 2 bits. We must parse this result as binary with bit fields. This is not as convenient as parsing without bit fields but not uncommon for binary packet protocols especially. It is not unreasonable or uncommon to expect a binary protocol parser to deal with bit fields whereas it would be unreasonable to expect a text domain parser to deal with bit fields. To convert to (dc, rm) form from this binary form we must first mask off or extract the first 6 bits. These we convert through the standard Base64URL table back to the 1 character dc code. The remaining 18 bits are shifted 2 bits to the right. The last two bytes are the rm. Thus conversion back to (dc, rm) form involves extracting a 6 bit field and a shift.  

Similarly for a 2 character dc, conversion involves extracting 2 6 bit fields and shifting 4 bits to the right. 

Finally for a 4 character dc, conversion involves extracting 4 6 bit fields or 3 bytes and no shifts.

Any longer dc codes when combined with the converted cm  that result in primitives  in the textual domain that are both minimally sized and also satisfy the composition property must be of the following lengths 1, 2, 4, 5, 6, 8, 9, 10, 13 .... where the length of the dc code is determined by the number of pad bytes for the converted crypto material. We then have as a result another mapping pair. These we label *S2R* and *R2S* for streaming binary to raw binary and raw binary to streaming binary. In other words *S2R* goes from a streaming binary primitive to a tuple of *(dc, rm)* and *R2S* goes from a tuple *(dc, rm)* to a streaming binary primitive. This allows us to go full circle in either direction between the 3 formats. These paths are as follows:

*(dc, rm) -> R2T -> t -> T2S -> s -> S2R -> (dc, rm)*   

and  

*(dc, rm) -> R2S -> s -> S2T -> t -> T2R -> (dc, rm)*.  

The important properties are that conversion to from S and T domains is composable via concatention over the Base64 to/from binary conversion. We have stable code representations in T for readability and textual parsing. The stable codes enable the minimum sized composable primitives.


#### Direct Primitive Conversion to Binary from Unstable Textual Code

Here we make a comparison to alternative A) which we label the unstable derivation code representation. Suppose for comparison that an unstable representation also satisfies the composiblity property that is the combined code plus cryptographic material must be an integer multiple of 3 binary bytes and its dual representation in Base64 is an integer multiple of 4 Base64 characters. Similarly to B) the derivation code may be small, as little as 1 or 2 bytes. But regardless, in order to satisfy composiblity, the minimum possible total size of the combined primitive is still the same as A). So there is no size advantage of an unstable version over the stable version given they both satisfy composibility. The unstable version, however, has more code space because each code byte has available to it a full octet (8 bits) not merely a sextet (6 bits) per each Base64 code character. But as we will discuss below the full code space may not be usable if a parser needs to disambiguate between binary and Base64 streams or to parse othewise unframed cryptomaterial. Self-framing becomes more difficult in the text domain. 

Lets walk through equivalent examples but for an unstable coding scheme. Suppose we have a 1 byte derivaton code and 2 bytes of crypto material. The combined primitive is 3 bytes which converts as a whole to 4 Base64 characters. The code is split between the first two Base64 characters with the first 6 bits of the 1 byte code represented by the first Base64 character and the last 2 bits are mixed with the first 6 bits of the appended crypto material to provide the second character. The second character is unstable because its mixed and there is no way to predict the mixing because cryptomaterial is by nature pseudo random. The first character is also unstable in the sense that there are 4 different codes in the the 1 byte code table that share the first 6 bits. The only way to disambiguate is to either limit the code table to only use the first bits bits and treat the last 2 bits as padding. Or to extract both characters and do the appropriate bit field extraction and mapping. But this defeats the point of doing textual parsing. Consequently the typical approach is to always first convert the full primitive from Base64 back into binary. The the code byte or bytes may be simply extracted (they are stable in binary) and the remaining bytes are the crypto material. But this requires either framing or delimitation in the Base64 domain (which is the usual case but not very useful for KERI which wants self-framing in both binary and Base-64) or the Base64 to Binary takes a 4 character chunk and then converts that to three binary bytes and then from that chunk is able to determine how many more chunks are needed to get the full derivation code. If it is also assumed that the derivation code is not extensible then the number of bytes may be fixed and therefore the number of characters that need to be extracted to parse is also fixed. The advantage of the unstable approach is that once converted back to binary there are  no bit field shifts required. Thus the the composable binary representation is simpler to parse. The disadvantage of the unstable approach is that parsing effectivly must happen in the binary domain. Extensible variable length derivation codes, however, may be more difficult to parse and may be no less difficult than stable coding schemes.


### Comparative Examples

For example, did:key uses an essentially unstable approach its derivation code for its identfiers [[13]] but makes it stable (in the text domain) by prepending the character z to its derivation code and then the remaining bytes of its derivation code may only using printible text entries from the multicodec table [[10]][[11]][[12]]. So by limiting its code space to text printable entries it has stability in the text domain. The remaining crypto material is encoded in Base58Check which as mentioned previously is not composable like Base64 [[15]]. The minimum code size is 4 bytes that are also  4 printable text characters. So its minimum size is greater. Because the did:key scheme does not satisfy the composiblity constraint each identifier must always appear in a framed or delimited context but it is self-framing so it may be converted on a primitive by primitive basis but not as a composed group. It appears from the did:key spec that there is no contemplation that did:key identifiers would ever be used in a streamed binary application but would only ever appear in the text domain and then converted to binary not for streaming but to performa cryptographic operations. To restate, it not composable in the textual domain although it is stable. The did:key approach exposes some of the problems with multi-codec has some codes are text printable and some not so one one can only use a part of the code space when designing a protocol and as a result the minimum code size is larger than a more uniformly more compactly designed code approach.

Similarly did:peer uses a stable approach where the derivation code is expressed using some text printable characters followed by a Base58Check encoding of the raw cryptographic material [[14]]. It has similar comparable properties of longer minimum code size, stability given a subset of the MultiCodec table but non composable. It also appears from the did:peer spec that there is no contemplation that did:peer identifiers would ever be used in a streamed binary application but would only ever appear in the text domain and then converted to binary not for streaming but to performa cryptographic operations.

Neither did:key or did:peer anticipate using similarly compact prepended derivation code representations of other crypto material items such as digests, signatures, public keys etc. Clearly a scheme could be developed for either but nontheless would not be composable. 

## Summary

KERI's design both requires and benefits from a universal compact encoding for all cryptographic material items with stable self-framing textual derivation codes.  This compact encoding scheme fully supports both textual and binary streaming applications of attached crypto material of all types. This approach includes composability in both the textual and binary streaming domains. The primitives may be the minimum possible but composable size. Making composiblity a guaranteed property allows future extensible support of new compositions of streaming formats based on pre-existing core primitives and compositions of core primitives.


Cryptographic material in KERI has three primary representations or domains. These are as follows.

1- Separated code and raw material for crypto operations expressed as a tuple *(dc, rm)*, where *dc* is the derivation code and *rm* is the raw binary crypto material. Cryptographic operations demand the raw binary while the derivation code indicates what crypto suite of operatons to use. This is the best representation for performing the cryptographic operations. We label this the *'R'* domain for raw binary material for crypto operations.

2- Test based primitive composed of a prepended base64 code and appended base64 crypto material. This is used in namespaces and is the identifier native domain but also supports text streaming replay transmission and storage. Base64 is the best practical representation for namespace compatibility and useability. We label this the *'T'* domain (for text).

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









##  Derivation Codes


We have already established the potential usefulness of flexible primitive preserving stream composition across the transformations between domains as well as the importance of using binary streaming for reducing the bandwidth of of attached crypto material in KERI. But what complexity does this bring to the coding scheme for derivation codes.

But what does it mean for creating binary versions of events not merely attached signatures in receipts. We have a toolkit for creating an extensible binary event encoding. Main reason for using JSON, CBOR and MsgPack is they are extensible enveloping encoding encodings. But given the limited number fields and data btypes and the preponderance of crypto material in KERI   streaming e

But what complexity does this bring to the coding scheme for derivation codes.



KERI supports two formats for fully qualified cryptographic material. These are Base64 on 6 bit boundaries per character and Base2 on 8 bit boundaries per byte. Base64 is the most compact URL/File/Textual format. Base 2 with 8 bit boundaries is the most generally useful binary format. The coding is designed so that a base 2 stream with 8 bit boundaries and a base 64 stream with 6 bit boundaries have perfect boundaries for both. The number of Base 64-6bit characters is 4/3 of the number of base2-8bit bytes. Likewise the number base 2-8bit bytes is 3/4 the number of Base 64-6bit characters.

The base 64 standard adds pad characters to ensure these perfect boundaries. KERI uses these base64 pad characters opportunistically. In most cases, this means, zero overhead for its derivation code. Its worst case (for now) is 3 additional bytes (4 base 64 characters) for a derivation code when there are no pad characters on the base material. This case is comparable to a Multi-Codec with function, base, and length bytes. Also there is no assurance of perfect boundaries with multi-codec between Base64-6bit and Base2-8bit for a given base material length, which means that pad characters may be needed in addition to the MultiCodec characters. This further increases the average length for multi-codec over KERI.

Furthermore, anything that has perfect boundaries with divisor of 3 base2-8 bit and 4 base64-6 bit may also have perfect boundaries for both. This includes Hex (4 bit boundaries) and octal (3 bit boundaries). For example, 24 bits = 3x8bits = 4x6bits = 6X4bits =8X3bits. So KERI derivation codes satisfy the major binary representations. Perfect boundaries means conversion from characters streams to binary streams is optimized for transmission and processing. Eventually, as KERI becomes widely used, it is anticipated that full binary implementations of KERI will result. These binary representations will benefit from the ability to leverage crypto-graphic material streams (character or byte) that always align on perfect boundaries which should result in significant performance optimizations.




The IPFS Multicodec tables are an example [[10]][[11]][[12]][[13]]. The usally use of multi-codec first prepend the code to the raw binary and then convert the concatenated whole to Base64. As pointed out previously this has the disadvantage of an unstable Base64 representation of the trailing characters of any prepended code due to mixing bits with the following cryptographic material except when the code is an integral multiple of three bytes. The Multicodec table is large and expanding and captures many more use cases than KERI needs and is also not yet stable in terms of values. Each implementation often adds on their own codes and creates a custom version of the multicodec table [[13].  




Attached Crypto is not verifiable but used to verify events.
So its integraity does not need to be established like an event

Base64 in framed eveneloped form can ignore Pad Bytes but Base64 not in framed can't ignore pad bytes

For compactness Context determines semantics of derivation code not merely code on its own

De don't embed context in the derivation code. This makes code more compact. Contexts also may evolve over time and we want codes to be stable.

Set of derivation code tables interpreted as a crypto operation on a size of crypto material in a context

To help with context we have  groupe tables.

thousands of receipts or endorsements

Firt Hextet or Char is unique in composition code (framing) counter is like Byte Order Mark to indicate big endian or little endian. Use to determine is binary or Base64








  3 to 12 character Base64 code. But only if one does not want stable expression of the algorithm code equivalent and the hash length code equivalent via integral separation of the resultant characters and then separation from the appended Base64 crypto material. This is a problem whenever the size of the multihash codes are not an integral multiple of 3 bytes in binary or 4 characters in Base64. The only way to ensure this is either to use Base64 pad characters or to use a non-standard application of multihash where one does a custom mapping Base64 table.







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


## Notes:

Latex:  https://www.codecogs.com/latex/eqneditor.php  

x_{}^{t}

x_{}^{s}

x_{}^{t} =T\left ( x_{}^{s} \right )

x_{}^{s} =S\left ( x_{}^{t} \right )

x_{}^{t}+y_{}^{t} =T\left ( x_{}^{s}+y_{}^{s} \right )

x_{}^{s}+y_{}^{s} =S\left ( x_{}^{t}+y_{}^{t} \right )

\sum_{i=0}^{N-1}x_{i}^{}

S\left (\sum_{i=0}^{N-1}x_{i}^{t}  \right ) =\sum_{i=0}^{N-1}x_{i}^{s}

T\left (\sum_{i=0}^{N-1}x_{i}^{s}  \right ) =\sum_{i=0}^{N-1}x_{i}^{t}



