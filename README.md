# odysseus-snap

Snap packaging for [Odysseus](https://github.com/pewdiepie-archdaemon/odysseus), a self-hosted AI workspace.

## Install

```
sudo snap install odysseus --classic
```

## Usage

Start the server:

```
odysseus
```

Then open **http://localhost:7000** in your browser.

### Options

| Environment variable | Default       | Description                         |
|----------------------|---------------|-------------------------------------|
| `ODYSSEUS_HOST`      | `127.0.0.1`   | Interface to bind (use `0.0.0.0` for LAN access) |
| `ODYSSEUS_PORT`      | `7000`        | Port to listen on                   |

### Configuration

Place a `.env` file at `~/snap/odysseus/common/.env` before starting the server.
All variables from the upstream [`.env.example`](https://github.com/pewdiepie-archdaemon/odysseus/blob/dev/.env.example) are supported:

```
OPENAI_API_KEY=sk-...
LLM_HOST=localhost
AUTH_ENABLED=true
```

### Data

User data (conversations, uploads, settings, search cache) is stored in:

```
~/snap/odysseus/common/app/
```

This directory persists across `snap refresh` — only the Python source code is updated on refresh, never your data.

## Build

Requires [snapcraft](https://snapcraft.io/snapcraft).

```
snapcraft
sudo snap install odysseus_*.snap --classic --dangerous
```

## Reporting issues

Please open issues at https://github.com/kenvandine/odysseus-snap/issues.

For bugs in Odysseus itself, use https://github.com/pewdiepie-archdaemon/odysseus/issues.
