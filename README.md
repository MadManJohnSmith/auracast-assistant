# auracast-assistant

An open-source **Auracast assistant** for Linux: discover, list, and join
Bluetooth LE Audio broadcast streams (Auracast) from the command line — with
a GUI later.

## Why

The Linux LE Audio stack (kernel ISO sockets, BlueZ BAP/BASS, PipeWire) is
maturing fast — but the top layer is unfinished: the assistant that scans for
nearby broadcast sources, presents them with names and quality, handles
broadcast codes, and joins a stream. Collabora's own engineering report marks
assistant / scan-delegator UX as high-priority future work, and fresh open
BASS issues confirm nobody has the experience resolved yet. Today there is no
polished CLI or GUI for this on Linux.

## Status

**Planning.** Next steps:

1. Hardware survey: verify local adapter LE Audio capabilities (ISO/BAP).
2. Reproduce the current stack state on this machine (BlueZ version,
   experimental flags, PipeWire roles).
3. Draft and stabilize the CLI contract.

## Planned CLI (draft, may change)

```text
auracast scan [--timeout SEC]              # list nearby broadcast sources
auracast info <source-id>                  # name, quality, encryption state
auracast join <source-id> [--code CODE]    # sync BIG, hand stream to PipeWire
auracast leave
```

## References

- Collabora — Implementing Bluetooth LE Audio and Auracast on Linux systems
  (2025-11-24 engineering report)
- BlueZ 5.86–5.88 release notes (Enhanced BAP, VCP, MCP, TMAS)
- Bluetooth SIG — Auracast program

## License

[Apache-2.0](LICENSE)
