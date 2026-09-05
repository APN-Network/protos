# Protobuf Defs

[![buf](https://github.com/APN-Network/protos/actions/workflows/buf.yml/badge.svg)](https://github.com/APN-Network/protos/actions/workflows/buf.yml)

These [Protocol Buffers] definitions describe the messages
  that APN clients and servers exchange.
The programs on both ends are closed-source;
  the definitions are published here on their own,
  so that anyone can read and review the protocol they speak.

Several private repositories consume this one as a Git submodule
  and generate their bindings from it.
It is not a general-purpose library,
  and nothing here is guaranteed to stay stable
  outside of that use.

Please do not send pull requests.
Every change to a message has to land together with the code
  that implements it on both sides of the wire,
  so a patch on its own cannot be merged.
If you spot a mistake or a weakness in the protocol,
  open an issue and describe it — that is the feedback we want.

## Addresses

An address the client dials, or writes onto its own interface,
  is raw bytes in network byte order —
  four for IPv4, sixteen for IPv6.
`Welcome.ip`, `Welcome.home` and `Peer.ip` are the shape to copy.

A prefix stays text in CIDR form,
  because it carries a length beside the address
  and because one list mixes both families:
  see `Whitelist.prefixes` and `Welcome.subnet`.

A map key stays text whatever it names,
  since proto3 allows only integral and string keys.
That is why `Ping.canaries` is keyed by a dotted address
  and asks the client to convert `Peer.ip` before inserting it.

Two fields predate this rule and contradict it.
`Owned.ip` is dotted text although the client dials it,
  and `Welcome.dns` is textual although the client hands it
  to its own resolver configuration.
Both stay as they are,
  because every client already speaks them
  and rewriting the wire would buy no behaviour.

A new field that departs from the rule must say why in its comment.

[Protocol Buffers]: https://protobuf.dev/
