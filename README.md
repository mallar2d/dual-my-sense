# Dual My Sense (Dualsensectl GUI)

A simple Rust GUI wrapper around the `dualsensectl` CLI for Linux. It exposes most commands via a friendly interface built with `egui/eframe`.

## Build & Run

Requires Rust (stable) and the `dualsensectl` binary available in PATH.

```fish
# from this folder
cargo run --release
```

If `dualsensectl` needs udev permissions, follow the udev rules from its README.

## Notes

- Device picker uses `dualsensectl -l` output; selecting "(auto)" omits `-d`.
- Log panel shows commands and outputs.
- Trigger tab supports common modes and a custom mode with free params.
- Monitor can run without or with a shell command; it sets `$DS_DEV` so your command can detect the device.

MIT.
