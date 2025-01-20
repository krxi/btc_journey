

Bitcoin nodes actually uses this structure for broadcast message.

```
Header:  F9BEB4D976657273696F6E0000000000550000002C2F86F3
Payload: 7E1101000000000000000000C515CF6100000000000000000000000000000000000000000000FFFF2E13894A208D000000000000000000000000000000000000FFFF7F000001208D00000000000000000000000000
```

The header contains a summary of the message, and this structure is same for every bitcoin protocol.

```
Header: (version message)
┌─────────────┬──────────────┬───────────────┬───────┬─────────────────────────────────────┐
│ Name        │ Example Data │ Format        │ Size  │ Bytes                               │
├─────────────┼──────────────┼───────────────┼───────┼─────────────────────────────────────┤
│ Magic Bytes │              │ bytes         │     4 │ F9 BE B4 D9                         │
│ Command     │ "version"    │ ascii bytes   │    12 │ 76 65 72 73 69 6F 6E 00 00 00 00 00 │
│ Size        │ 85           │ little-endian │     4 │ 55 00 00 00                         │
│ Checksum    │              │ bytes         │     4 │ F7 63 9C 60                         │
└─────────────┴──────────────┴───────────────┴───────┴─────────────────────────────────────┘
```

**Magic bytes:** This is unique set of bytes used to identfythe start of a new message. they are always same. Its main purpose is selecting network protocol. like regtest, testnet, mainnet

**Command:** This indicates the type of message being sent. You can send different types of messages in Bitcoin protocol, and they contain diffrent types of information. It's a 12-byte field containing the ascii encoding of the name of the message type.

**Size:** This is the size of the upcoming payload. This indicates how many bytes you need to read  from the socket to get full message being sent.

**Checksum:** This is a small fingertprint for the payload.