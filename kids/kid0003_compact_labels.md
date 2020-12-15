---
tags: KERI
email: sam@samuelsmith.org
---

# KID0003  Subsection Compact Labels



There does not seem to be any objection to 1 char labels when it is clear from context. Although it does create more friction in picking labels due to the limited choices.  Here is a revised version of Steve's list.  

The revised Table does not use the same label for more than one type of value. This completely avoids ambiguity. 

## Tables of Element Labels from all messages and seals

|Label|Description|Proposed|Notes|
|---|---|---|---|
|vs|Version String| v |
|pre|Identifier Prefix| i |
|sn|Sequence Number| s |
|ilk|Message Type| t |  
|dig| Event Digest, Seal Digest|d|  d for digest universal, type is clear from context except one |
|dig| Prior event digest | p| 
|sith|Signing Threshold, Keys Element Threshold |kt|  uses k from the keys field for the threshold|
|keys|List of Signing Keys| k |
|nxt|Next Key Set Commitment| n |
|toad|Threshold of Accountable Duplicity, Witness Threshold| wt |
|wits|List of Witnesses| w |
|cnfg|Configuration Data List| c |
|cuts|List of Witnesses to Cut Remove| wr |  witness cut  w- is not allowed as an attributed which would break a dict to object map
|adds|List of Witnesses to Add| wa | witness add w+ is not allow as an attribute which would break a dict to object map
|data|Payload Data List (Seal List) anchor list |a|
|trait|Configuration Trait|ct| may not need if adopt change in structure of  cnfg list|
|seal| Seal | a | a for anchor, seals are a type of anchor, seal  type is clear from context
|root|Merkle Tree Root Digest|rd|  only context where digest type is not clear |
|EstOnly|Establishment Only| eo | 
|| Last received Event in key state | e|
||Last Establishment Event in key state| ee |
||Delegator Identifier  Prefix key state| di |
|| Delegatore Location Seal Anchor. | da |
|| Version Number | vn |  only the major.minor version number from version string |


## Seal Usages of Labels
Seals are mappings. There are 4 types of seals and one event reference that functions as a seal. The event reference is the last establishment event in the key state message. So I include it here for completeness.

Digest 
Merkle Root Digest
Event Digest
Event location Digest
Last Event

|Label|Description|Proposed|Notes|
|---|---|---|---|
| pre | identifier prefix of KEL for event | i|
| sn |  sequence number of event | s |
| ilk |  message type  of event | t |
| dig | digest depends on context | d |
| dig | prior event digest depends on context | p |
| root |  merkle tree root digest  | rd |

Digest Seal has only one element
```JSON
{
    "d": "Eabcde..."
}
```

Merkle Tree Root Digest Seal has only one element (hence is ambiguous wrt to digest seal
```json
{
    "rd": "Eabcde..."
}
```

Event Seal has 3 elements
```json
{
    "i": "Ebietyi....",
    "s": "3",
    "d": "Eabcde..."
}
```

Event location Seal has 4 elements
```json
{
    "i": "Ebietyi....",
    "s": "3",
    "t":  "ixn",
    "p": "Eabcde..."
}
```

Last  Received Event Reference in KeyState has 3 elements
```json
{
   "s": "2",
   "t": "ixn",
   "d": "E4u8kd..."
}
```

Last  Establishment Event Reference in KeyState has 2 elements
```json
{
   "s": "2",
   "d": "E4u8kd..."
}
```

## Message Usage of Labels

### Inception Event

```json
{
    "v" : "KERI10JSON00011c_",
    "i" : "EZAoTNZH3ULvaU6Z-i0d8JJR2nmwyYAfSVPzhzS6b5CM",
    "s" : "0",
    "t" :  "icp",
    "kt":  "1",
    "k" :  ["DaU6JR2nmwyZ-i0d8JZAoTNZH3ULvYAfSVPzhzS6b5CM"],
    "n" :  "EZ-i0d8JZAoTNZH3ULvaU6JR2nmwyYAfSVPzhzS6b5CM",
    "wt":  "1",
    "w" : ["DTNZH3ULvaU6JR2nmwyYAfSVPzhzS6bZ-i0d8JZAo5CM"],
    "c" :  ["eo"]
}
```

### Rotation Event  (also delegating rotation)

```json
{
    "v" : "KERI10JSON00011c_",
    "i" :  "EZAoTNZH3ULvaU6Z-i0d8JJR2nmwyYAfSVPzhzS6b5CM",
    "s" : "1",
    "t" :  "rot",
    "p" : "EULvaU6JR2nmwyZ-i0d8JZAoTNZH3YAfSVPzhzS6b5CM",
    "kt" :  "1",
    "k" :  ["DaU6JR2nmwyZ-i0d8JZAoTNZH3ULvYAfSVPzhzS6b5CM"],
    "n" :  "EYAfSVPzhzZ-i0d8JZAoTNZH3ULvaU6JR2nmwyS6b5CM",
    "wt":  "1",
    "wa":  ["DTNZH3ULvaU6JR2nmwyYAfSVPzhzS6bZ-i0d8JZAo5CM"],
    "wr":   ["DH3ULvaU6JR2nmwyYAfSVPzhzS6bZ-i0d8TNZJZAo5CM"],
    "a" : 
            [
               {
                   "i": "EJJR2nmwyYAfSVPzhzS6b5CMZAoTNZH3ULvaU6Z-i0d8", 
                   "s": "0",  
                   "d": "ELvaU6Z-i0d8JJR2nmwyYAZAoTNZH3UfSVPzhzS6b5CM"
               }
            ]
}
```

### Interaction Event  (Also delegating Interaction)

```json
{
    "v" : "KERI10JSON00011c_",
    "i" :  "EZAoTNZH3ULvaU6Z-i0d8JJR2nmwyYAfSVPzhzS6b5CM",
    "s" : "2",
    "t" :  "isn",
    "p" : "EULvaU6JR2nmwyZ-i0d8JZAoTNZH3YAfSVPzhzS6b5CM",
    "a" : 
            [
               {
                   "i": "EJJR2nmwyYAfSVPzhzS6b5CMZAoTNZH3ULvaU6Z-i0d8", 
                   "s": "1",  
                   "d": "ELvaU6Z-i0d8JJR2nmwyYAZAoTNZH3UfSVPzhzS6b5CM"
               }
            ]
}
```

### Delegated Inception Event

```json
{
    "v" : "KERI10JSON00011c_",
    "i" :  "EJJR2nmwyYAfSVPzhzS6b5CMZAoTNZH3ULvaU6Z-i0d8",
    "s" : "0",
    "t" :  "dip",
    "kt":  "1",
    "k" :  ["DaU6JR2nmwyZ-i0d8JZAoTNZH3ULvYAfSVPzhzS6b5CM"],
    "n" :  "EZ-i0d8JZAoTNZH3ULvaU6JR2nmwyYAfSVPzhzS6b5CM",
    "wt":  "1",
    "w" : ["DTNZH3ULvaU6JR2nmwyYAfSVPzhzS6bZ-i0d8JZAo5CM"],
    "c" :  [],
    "da" :  
           {
             "i":  "EZAoTNZH3ULvaU6Z-i0d8JJR2nmwyYAfSVPzhzS6b5CM",
             "s": "1",
             "t": "rot",
             "p": "E8JZAoTNZH3ULZ-i0dvaU6JR2nmwyYAfSVPzhzS6b5CM"
           }
}
   
```

### Delegated Rotation Event

```json
{
    "v" : "KERI10JSON00011c_",
    "i" :  "EZAoTNZH3ULvaU6Z-i0d8JJR2nmwyYAfSVPzhzS6b5CM",
    "s" : "1",
    "t" :  "rot",
    "p" : "EULvaU6JR2nmwyZ-i0d8JZAoTNZH3YAfSVPzhzS6b5CM",
    "kt" :  "1",
    "k"  :  ["DaU6JR2nmwyZ-i0d8JZAoTNZH3ULvYAfSVPzhzS6b5CM"],
    "n"  :  "EYAfSVPzhzZ-i0d8JZAoTNZH3ULvaU6JR2nmwyS6b5CM",
    "wt":  "1",
    "wa":  ["DTNZH3ULvaU6JR2nmwyYAfSVPzhzS6bZ-i0d8JZAo5CM"],
    "wr":   ["DH3ULvaU6JR2nmwyYAfSVPzhzS6bZ-i0d8TNZJZAo5CM"],
    "a" : [ ],
    "da" :  
           {
             "i":  "EZAoTNZH3ULvaU6Z-i0d8JJR2nmwyYAfSVPzhzS6b5CM",
             "s": "1",
             "t": "isn",
             "p": "E8JZAoTNZH3ULZ-i0dvaU6JR2nmwyYAfSVPzhzS6b5CM"
           }
}
```

### Non-Transferable Prefix Signer Receipt

```json
{
  "v"   : "KERI10JSON00011c_",
  "i"  : "AaU6JR2nmwyZ-i0d8JZAoTNZH3ULvYAfSVPzhzS6b5CM", 
  "s"   : "1", 
  "t"  : "rct",
  "d"  : "DZ-i0d8JZAoTNZH3ULvaU6JR2nmwyYAfSVPzhzS6b5CM" 
}
```

### Transferable Prefix Signer Receipt
```json
{
  "v"   : "KERI10JSON00011c_",
  "i"  : "AaU6JR2nmwyZ-i0d8JZAoTNZH3ULvYAfSVPzhzS6b5CM", 
  "s"   : "1",  
  "t"  : "vrc", 
  "d"  : "DZ-i0d8JZAoTNZH3ULvaU6JR2nmwyYAfSVPzhzS6b5CM", 
  "a" :
          {
             "i"  : "AYAfSVPzhzS6b5CMaU6JR2nmwyZ-i0d8JZAoTNZH3ULv",  
             "s":  "4",
             "d" : "DZ-i0d8JZAoTNZH3ULvaU6JR2nmwyYAfSVPzhzS6b5CM",  
           }
}
```

### Non-transferable Prefix Signer Key State Message

While the actual Key State only needs the version number, that message itself needs the full version string so that it can be parsed when sent over the wire using low level TCP etc to support all the serializations.  A different version of the message could be used with a higher level transport such as JSON only ReST. In that case then the "v" could be replaced with "vn" = "1.0" for example.

```json
{
  "v"   : "KERI10JSON00011c_",  
  "i"  : "EaU6JR2nmwyZ-i0d8JZAoTNZH3ULvYAfSVPzhzS6b5CM",  
  "t"  : "ksn",  
  "kt" : "1", 
  "k" : ["DaU6JR2nmwyZ-i0d8JZAoTNZH3ULvYAfSVPzhzS6b5CM"],  
  "n"  : "EZ-i0d8JZAoTNZH3ULvaU6JR2nmwyYAfSVPzhzS6b5CM",  
  "wt" : "1",  
  "w" : ["DnmwyYAfSVPzhzS6b5CMZ-i0d8JZAoTNZH3ULvaU6JR2"], 
  "c" : ["eo"],
  "e":
        {
            "s": "0",
            "t": "rot",
            "d" :  "EAoTNZH3ULvaU6JR2nmwyYAfSVPzhzZ-i0d8JZS6b5CM", 
        },
  "ee" : 
         {
           "s":  "1",
           "d":  "EAoTNZH3ULvaU6JR2nmwyYAfSVPzhzZ-i0d8JZS6b5CM"
          },
  "di": ""
}

```

### Transferable  Prefix Signer Key State Message

While the actual Key State only needs the version number, that message itself needs the full version string so that it can be parsed when sent over the wire using low level TCP etc to support all the serializations.  A different version of the message could be used with a higher level transport such as JSON only ReST. In that case then the "v" could be replaced with "vn" = "1.0" for example.

```json

{
  "v"   : "KERI10JSON00011c_",  
  "i"  : "EaU6JR2nmwyZ-i0d8JZAoTNZH3ULvYAfSVPzhzS6b5CM",  
  "t"  : "kst",   
  "kt" : "1",  
  "k" : ["DaU6JR2nmwyZ-i0d8JZAoTNZH3ULvYAfSVPzhzS6b5CM"],  
  "n"  : "EZ-i0d8JZAoTNZH3ULvaU6JR2nmwyYAfSVPzhzS6b5CM",  
  "wt" : "1", 
  "w" : ["DnmwyYAfSVPzhzS6b5CMZ-i0d8JZAoTNZH3ULvaU6JR2"], 
  "c" : ["eo"], 
  "e":
        {
            "s": "0",
				  "t": "rot",
            "d" :  "EAoTNZH3ULvaU6JR2nmwyYAfSVPzhzZ-i0d8JZS6b5CM", 
        },
  "ee" : 
         {
           "s":  "1",
           "d":  "EAoTNZH3ULvaU6JR2nmwyYAfSVPzhzZ-i0d8JZS6b5CM"
          },
  "di": "",
  "a":
         {
             "i":  "EJZAoTNZH3ULvYAfSVPzhzS6b5aU6JR2nmwyZ-i0d8CM",
              "s":  "1",
              "d":  "EULvaU6JR2nmwyAoTNZH3YAfSVPzhzZ-i0d8JZS6b5CM"
        }
}

