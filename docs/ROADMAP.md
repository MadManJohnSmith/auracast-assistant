# ROADMAP — auracast-assistant

Goal: the missing top layer of Linux LE Audio — an assistant that makes
Auracast broadcast discovery and joining usable from the terminal first,
then a GUI.

## Phase 0 — Hardware and stack survey

- Verify adapter capabilities: ISO support, controller roles, kernel config.
- Record the exact stack state: BlueZ version and experimental features,
  PipeWire version, bluetoothd flags.
- Output: `docs/hardware-survey.md` with observed facts only.

**Acceptance:** a reproducible survey on at least one machine, stating
clearly what is supported today.

## Phase 1 — Join an existing broadcast with what exists

- Use current BlueZ BAP/BASS APIs to discover and join a broadcast source
  (a second LE Audio transmitter or phone app as the source).
- Measure what is missing at each step; file notes upstream rather than
  patching privately first.

**Acceptance:** scripted join of one unencrypted broadcast; written gap list.

## Phase 2 — CLI

- `scan` / `info` / `join` / `leave` as drafted in the README, over BlueZ
  D-Bus APIs; hand the decoded stream to PipeWire.
- Encrypted broadcast: broadcast code entry flow.

**Acceptance:** stable CLI joining both unencrypted and code-protected
broadcasts; errors are actionable, not stack traces.

## Phase 3 — Assistant experience

- Persistent discovery with human-readable listing, quality/codec metadata,
  source bookkeeping.
- Scan Delegator role support (join on behalf of another device) if the
  stack permits.

**Acceptance:** a new user can go from zero to listening with one command
and no stack archaeology.

## Phase 4 — GUI

- Desktop UI over the CLI core.

## Companion slice (optional, separate effort)

- Vendor control channel RE for LE Audio mode earbuds via GATT (btsnoop HCI
  capture vs. vendor app). Kept in a separate directory/repo to avoid
  entangling it with the assistant's clean-room stack work.
