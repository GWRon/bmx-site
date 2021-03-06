---
id: brl.base64
title: BRL.Base64
sidebar_label: BRL.Base64
---


Base64 is an encoding scheme that represents binary data in ASCII format. Three 8-bit bytes of data (24-bits) is represented in Base64 by four 6-bit characters.

Base64 is commonly used when there is a need to store or transfer binary data using textual media.

A quote from Linus Torvalds :

> Crying that it's an application bug is like crying over the speed of light: you should deal with reality, not what you wish reality was.

contains a sequence of 8-bit characters. Encoded as Base64 results in the following text :
```
Q3J5aW5nIHRoYXQgaXQncyBhbiBhcHBsaWNhdGlvbiBidWcgaXMgbGlrZSBjcnlpbmcgb3ZlciB0
aGUgc3BlZWQgb2YgbGlnaHQ6IHlvdSBzaG91bGQgZGVhbCB3aXRoIHJlYWxpdHksIG5vdCB3aGF0
IHlvdSB3aXNoIHJlYWxpdHkgd2FzLg==
```

Padding (`=`) is added to make the last encoded block 4 Base64 characters.

Note that the Base64 encoded text wraps at character 76. This was typically originally applied when Base64 was used to attach files to emails.
When encoding, you can set the option `EBase64Options.DontBreakLines` if you'd prefer to have the data encoded into a single, long line of text.




## Types
| Type | Description |
|---|---|
| [TBase64](../../brl/brl.base64/tbase64) | Encode/Decode Base64 data. |

## Enums
| Enum | Description |
|---|---|
| [EBase64Options](../../brl/brl.base64/ebase64options) | TBase64 options. |

