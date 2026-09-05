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

[Protocol Buffers]: https://protobuf.dev/
