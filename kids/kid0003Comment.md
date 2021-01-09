
# KID0003 - Serialization Commentary

[![hackmd-github-sync-badge](https://hackmd.io/nhNY3H3aS4qjMipjJvWB7g/badge)](https://hackmd.io/nhNY3H3aS4qjMipjJvWB7g)

## Navigation

[Back to table of contents](/readme.md)
|Link|Section|Commentary|
|---|---|---|
|[0000](kid0000.md)|Glossary, overview, how to use||[0000Comment](kid0000Comment.md)|
|[0001](kid0001.md)|Prefixes, Derivation and derivation reference tables||[0001Comment](kid0001Comment.md)|
|[0002](kid0002.md)|Data model (field & event concepts and semantics)|0002Comment|
|[0003](kid0003.md)|Serialization|0003Comment|
|[0004](kid0004.md)|Key Configuration (Signing threshold & key set)|0004Comment|
|[0005](kid0005.md)|Next Key Commitment (Pre-Rotation)|0005Comment|
|[0006](kid0006.md)|Seals|[0006Comment](kid0006Comment.md)|
|[0007](kid0007.md)|Delegation (pending PR by Sam)|[0007Comment](kid0007Comment.md)|
|[0008](kid0008.md)|Key-Event State Machine|0008Comment|
|[0009](kid0009.md)|Indirect Mode & Witnesses|[0009Comment](kid0009Comment.md)|
|0010|Recovery/consensus Algorithm (KAACE)|0010Comment|
|0010|Database & Storage Considerations|0010Comment|
|0097|**Non-Normative** Implementation Guidance|n/a|
|0098|Use Cases|n/a|
|0099|Test Vectors and Normative Statement Index|n/a|

### Further rationale for serialization approach

Beneficial if not necessary constraints are ease and convenience of development and maintenance of the associated code libraries. One possibility that was considered and rejected would be to use same serializations for both the complete event serialization and the extracted data set serialization. The problem with that approach is that on an event by event basis the serialization encoding may change, that is, one event may be encoded using JSON and another using CBOR. This would require keeping track of which encoding was used on the event in order to reproducibly perform an extracted data serialization. More problematic is that for delegated events, the extracted data set digest included in one event may be from data extracted from an event belonging to a different identifier. In such a situation, keeping track of the encoding provides an inconvenience that obviates the advantages of using the same encodings for both events and extracted data sets. Given this, then a simplified but repeatable encoding algorithm may be used for the extracted data set serializations. Simplified because the extracted data sets do not need to be de-serialized.

The one constraint for extracted data set serializations is that the ordering of elements be exactly specified. One way to simplify that specification is to use the ordering of data elements in the complete event serialization. But this means imposing an ordering constraint on the complete event serialization. The advantage is that ordering is only expressed once per event not once per extracted data set. This better future proofs the protocol as there is always only one place for ordering and that is the complete event element ordering.

Another benefit of ordering the complete event serialization is that automated self-contained discovery of the serialization encoding used in an event becomes trivialized by requiring that the first element in the serialization be the version string element. A de-serializer may then unambiguously determine the encoding by inspecting the first few bytes of any serialized event. This better supports a wider variety of transport protocols and databases.

Until recently native JSON serialization libraries in JavaScript did not preserve a logical ordering of elements from a Mapping (JavaScript Object) data structure. The only ordering possible was lexicographic by sorting the fields in the mapping by their labels. This meant that arbitrary logical ordering of mapping fields was not possible and no semantic meaning could be imposed on the serialization based on order of appearance of fields. One could approximate some ordering by imposing lexicographic constraints on the field names but that makes the field names less usable. Ordered mappings support a logical ordering by preserving the order of creation of fields in the mapping. Any arbitrary order may be imposed by changing the order of creation of the fields in the mapping.

Fortunately Javascript ES6 (ES2015) and later now provide a mechanism to impose property (field) creation order on JSON.stringify() serializations. The latest versions of Javascript now natively preserve property creation order when serializing. This means that de-serialization will automatically recreate the properties in the same order as serialized. For those implementations of Javascript ES6 or later that do not yet support native JSON.stringify property creation ordering, a JSON.stringify parameter replacer function that uses the [[ownPropertyKeys]] internal method, namely, Reflect.ownKeys(object) may be employed to ensure property creation order. This means that native Javascript support may be easily and broadly provided. All major JavaScript implementations now support JavaScript ES6. Example JavaScript code is provided later in this document.

Other languages like Python, Ruby, Rust etc. have long supported native creation order preserving serializations of ordered mappings. These preserve field element (property equivalent) creation order. This in combination with the recent JavaScript support means that KERI may impose an ordering constraint on complete event data elements that may be used for canonical ordering of both complete events and extracted data element sets.