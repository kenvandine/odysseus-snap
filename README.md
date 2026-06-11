# odysseus snap

Snap packaging for [Odysseus](https://github.com/pewdiepie-archdaemon/odysseus) — a privacy-focused, self-hosted AI workspace with a browser UI.

## Building

```
snapcraft
```

Snapcraft builds Odysseus from source into a self-contained Python virtualenv (bundling the Python 3.12 stdlib so the snap does not depend on the host's Python) and bundles Node.js for the optional Browser MCP server.

## Installing

```
sudo snap install --classic odysseus_<version>_amd64.snap --dangerous
```

## Usage

Start the server, then open **http://localhost:7000** in your browser:

```
odysseus
```

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

User data (conversations, uploads, settings, search cache) is stored in `~/snap/odysseus/common/app/` and persists across `snap refresh` — only the Python source is updated on refresh, never your data.

## Design notes

**Self-contained Python** — The app runs from a bundled virtualenv that includes the Python 3.12 stdlib, so it works regardless of the host's system Python.

**Writable app copy** — On first run / refresh the read-only app source is copied to `$SNAP_USER_COMMON/app` so the app can write next to its own files.

**Classic confinement** — Odysseus needs broad filesystem access for documents, uploads, and tool execution.

## Links

- Upstream project: <https://github.com/pewdiepie-archdaemon/odysseus> (<https://pewdiepie-archdaemon.github.io/odysseus/>)
- Snap packaging: <https://github.com/kenvandine/odysseus-snap>
- Report a snap issue: <https://github.com/kenvandine/odysseus-snap/issues> (for bugs in Odysseus itself, use the [upstream tracker](https://github.com/pewdiepie-archdaemon/odysseus/issues))

## License

Odysseus is licensed under **AGPL-3.0**. This snap packaging lives in [kenvandine/odysseus-snap](https://github.com/kenvandine/odysseus-snap).
