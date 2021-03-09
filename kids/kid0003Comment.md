
# KID0003 - Serialization - Commentary

[![hackmd-github-sync-badge](https://hackmd.io/nhNY3H3aS4qjMipjJvWB7g/badge)](https://hackmd.io/nhNY3H3aS4qjMipjJvWB7g)

## Navigation

[Back to table of contents](readme.md)
|Link|Commentary|Section
|---|---|---|
|[0000](kid0000.md)|[X](kid0000Comment.md)|Glossary, overview, how to use|
|[0001](kid0001.md)|[X](kid0001Comment.md)|Prefixes, Derivation and derivation reference tables|
|[0002](kid0002.md)|[X](kid0002Comment.md)|Data model (field & event concepts and semantics)|
|[0003](kid0003.md)|X|Serialization|
|[0004](kid0004.md)|[X](kid0004Comment.md)|Key Configuration (Signing threshold & key set)|
|[0005](kid0005.md)|[X](kid0005Comment.md)|Next Key Commitment (Pre-Rotation)|
|[0006](kid0006.md)|[X](kid0006Comment.md)|Seals|
|[0007](kid0007.md)|[X](kid0007Comment.md)|Delegation (pending PR by Sam)|
|[0008](kid0008.md)|[X](kid0008Comment.md)|Key-Event State Machine|
|[0009](kid0009.md)|[X](kid0009Comment.md)|Indirect Mode & Witnesses|
|0010||Recovery/consensus Algorithm (KAACE)|
|0010||Database & Storage Considerations|
|0097|n/a|**Non-Normative** Implementation Guidance|
|0098|n/a|Use Cases|
|0099|n/a|Test Vectors and Normative Statement Index|

### Further rationale for serialization approach

Event serialization functions as both transport encoding and input data for cryptographic commitments. Event serializations are syntactically and semantically unique which provides a guarantee of non-collision in the space of Prefixes derived from them. This is a stronger guarantee than the one required for security, which is that the Prefix be uniquely bound to one set of supporting infrastructure (associated keys, witnesses and configuration). Note that one set of supporting infrastructure may have multiple Prefixes bound to it (e.g. by using the same event data with different serialization or derivation methods), but that this is not duplicitous.

The one constraint for cryptographically-bound data set (e.g. key event) serializations is that the ordering of elements be exactly specified. One way to simplify that specification is to use the ordering of data elements in the complete event serialization. But this means imposing an ordering constraint on the complete event serialization. The advantage is that ordering is only expressed once per event not once per extracted data set. This better future proofs the protocol as there is always only one place for ordering and that is the complete event element ordering.

Another benefit of ordering the complete event serialization is that automated self-contained discovery of the serialization encoding used in an event becomes trivialized by requiring that the first element in the serialization be the version string element. A de-serializer may then unambiguously determine the encoding by inspecting the first few bytes of any serialized event. This better supports a wider variety of transport protocols and databases.

### Further rationale for JSON.stringify usage

Until recently native JSON serialization libraries in JavaScript did not preserve a logical ordering of elements from a Mapping (JavaScript Object) data structure. The only ordering possible was lexicographic by sorting the fields in the mapping by their labels. This meant that arbitrary logical ordering of mapping fields was not possible and no semantic meaning could be imposed on the serialization based on order of appearance of fields. One could approximate some ordering by imposing lexicographic constraints on the field names but that makes the field names less usable. Ordered mappings support a logical ordering by preserving the order of creation of fields in the mapping. Any arbitrary order may be imposed by changing the order of creation of the fields in the mapping.

Fortunately Javascript ES6 (ES2015) and later now provide a mechanism to impose property (field) creation order on JSON.stringify() serializations. The latest versions of Javascript now natively preserve property creation order when serializing. This means that de-serialization will automatically recreate the properties in the same order as serialized. For those implementations of Javascript ES6 or later that do not yet support native JSON.stringify property creation ordering, a JSON.stringify parameter replacer function that uses the [[ownPropertyKeys]] internal method, namely, Reflect.ownKeys(object) may be employed to ensure property creation order. This means that native Javascript support may be easily and broadly provided. All major JavaScript implementations now support JavaScript ES6. Example JavaScript code is provided later in this document.

Other languages like Python, Ruby, Rust etc. have long supported native creation order preserving serializations of ordered mappings. These preserve field element (property equivalent) creation order. This in combination with the recent JavaScript support means that KERI may impose an ordering constraint on complete event data elements that may be used for canonical ordering of both complete events and extracted data element sets.

### Mutually Exclusive Multi-Type Support

Two event elements values may be of more than one type. The design decision was primarily practical. Although the idea of multiple types of values for a given element label introduces complexity it was less complexity then adding an additional element with unique label for each type.  

This trade-off happens with the value types are mutually exclusive. This means that should there be two different labels one for each type, then the presence of both labels must be handled. This is either an error or there must be a prioritization of
the labels. If both are present the implementation must decide which one is to be used. Clearly both should never be present so its an error. There is no way to infer the intent of the provider. But how best to enforce the error?  

The code to enforce mutual exclusivity is at least as complex as the code to do a type check switch.  In either case, because both types must separably supported, the code to support both types after the switch or prioritization is the same. But having only one field label with more than one type value means there is no chance of prioritization errors due to ambiguity of intent. One field forces zero ambiguity of intent. In languages like Python that are duck typed, the consensus is that a type switch is preferred to multiple fields.  

In general, an event's serialization should not be the operative representation. This distinction is not a problem for most languages, but does arise frequently in JavaScript where JSON is so closely tied to the operative representation. In non JavaScript implementations extraction from a serialization should handle the type switch and if desirable the representation after extraction may have multiple attribute labels, one for each value type.

In conclusion, the design decision here is that an OR-ing of value types in a serialization field element where those value types are mutually exclusive is practically less error prone and less complex than adding mutually exclusive field labels, one for each value type to the serialization.  


## Inception Configuration Traits

The naming of these as a "trait" was originally motivated by a desire to avoid confusion with  the words attribute and property refer to elements associated with objects (namely Python objects). However in other languages like Rust the word trait is also used. Another synonym "aspect" is used in other languages as well. So given there may not be a word with conflict, trait, is used because it is short. Given that the current trait is a *constraint* a suggested approach is to change the term to "curb" which does not conflict with any language terms.

Inception configuration traits only show up in the 'cnfg' element of the inception and delegated inception events.

So far the only configuration trait defined for KERI is the following:

```python
'EO'
```

The inception EO (Establishment Only) trait, when present places a constraint on the key event stream that only allows  establishment events. Or in other words interaction events are not allowed. This provides the best case security because signing keys become one use only and therefore minimizes the potential for exploit of signing keys.

To apply a trait include a mapping of the following form in the c (config) element list. Where the mapping has one element with key = 'trait' and value is the trait string. In this case value = 'EO'. For example:

```json
{

"c": [{"trait":  "EO"}]
}
```

Each trait string must be unique.

In delegated inception events additional traits may be defined for constraints on permissions. A suggested constraint maybe "DoNotDelegate" or "NoDel" to forbid the delegated event stream from creating delegations of other event streams.
