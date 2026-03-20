# rcpd

The daemon for [rcp](https://github.com/anotherSimpleCoder/rcp) — listens for incoming file transfers and saves them to disk.

## Installation

**Linux / macOS**

```sh
./install.sh
```

**Windows**

```powershell
.\install.ps1
```

Both scripts build the binary, create `~/.rcp/`, write a default `config.json`, and copy the binary there.

## Configuration

rcpd reads `config.json` from the working directory at startup. The install scripts place one at `~/.rcp/config.json`.

```json
{
  "port": 3000,
  "out_path": "/path/to/save/files"
}
```

| Field | Description |
|---|---|
| `port` | TCP port to listen on |
| `out_path` | Directory where received files are saved |

## Usage

Run rcpd from the directory containing `config.json`:

```sh
~/.rcp/rcpd
```

When a transfer arrives, a desktop dialog asks you to accept or decline. Accepted files are decompressed and written to `out_path`.

## Building from source

Requires [Rust](https://rustup.rs/).

```sh
cargo build --release
```

The binary will be at `target/release/rcpd`.
