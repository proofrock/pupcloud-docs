# 🏃 Running Pupcloud

Pupcloud is distributed as a single executable file. [Download and unpack the proper file for your OS/arch](../installation-and-building.md#installation).

Once done, just execute it with the directory to serve as an argument:

```bash
pupcloud -r /my/dir
```

Then, open `http://localhost:17178` with a browser. As simple as that!

Run`pupcloud --help` to see the other configuration options:

```
Pupcloud v0.8.0 (c) 2022 Germano Rizzo
Usage of ./pupcloud:
  -E, --allow-edits                 Allows changes to FS (default: don't)
      --allow-root                  Allow launching as root (default: don't)
      --bind-to string              The address to bind to (default "0.0.0.0")
      --follow-symlinks             Follow symlinks when traversing directories (default: don't)
      --max-upload-size int         The max size of an upload, in MiB (default 32)
  -P, --password string             The main access password, if desired. Use --pwd-hash for a safer alternative
  -p, --port int                    The port to run on (default 17178)
  -H, --pwd-hash string             SHA256 hash of the main access password, if desired
  -r, --root string                 The document root to serve
      --share-port int              The port of the sharing interface (default 17179)
      --share-prefix string         The base URL of the sharing interface (default: 'http://localhost:' + the port)
      --share-profile stringArray   Profile for sharing, in the form name:secret, multiple profiles allowed
      --share-profiles string       Profiles for sharing, in the form name:secret, multiple profiles comma-separated
      --title string                Title of the window (default "🐶 Pupcloud")
```

* enable "write" operations (delete/cut/paste/upload...;`-E` or `--allow-edits`);
* setup [authentication ](../authentication.md)(`-P` or `-H`);
* setup [folder sharing](../sharing-a-folder.md) (`--share-profile`/`--share-profiles`, `--share-port`, `--share-prefix`)
* specify a title/header for the web UI page (`--title`);
* use a different port then the default of 17178 (`-p`);
* bind to a network interface (`--bind-to`);
* instruct pupcloud to follow symlinks (`--follow-symlinks`);
* specify a maximum size for upload, in Megabytes (`--max-upload-size`).

By default, it's forbidden to run it as root. Use `--allow-root` if you (really) want to.

### Configure by env vars

Every CLI parameter can be specified via environment variable. If the corresponding env var is specified, it overwrites a CLI parameter. This is useful e.g. in Docker.

Env vars are mapped to CLI params as such:

| CLI Parameter         | Environment Variable | Example                               |
| --------------------- | -------------------- | ------------------------------------- |
| `--root`, `-r`        | `ROOT`               | `ROOT=./`                             |
| `--bind-to`           | `BIND_TO`            | `BIND_TO=192.168.1.0`                 |
| `--port`, `-p`        | `PORT`               | `PORT=8080`                           |
| `--title`             | `TITLE`              | `TITLE=WowSite`                       |
| `--password`, `-P`    | `PASSWORD`           | `PASSWORD=ciao`                       |
| `--pwd-hash`, `-H`    | `PWD_HASH`           | `PWD_HASH=5302bf`                     |
| `--allow-edits`, `-E` | `ALLOW_EDITS`        | `ALLOW_EDITS=1`                       |
| `--share-profile`     | _nothing_            |                                       |
| `--share-profiles`    | `SHARE_PROFILES`     | `SHARE_PROFILES=k1:v1,k2:v2`          |
| `--share-prefix`      | `SHARE_PREFIX`       | `SHARE_PREFIX=http://localhost:12345` |
| `--share-port`        | `SHARE_PORT`         | `SHARE_PORT=12345`                    |
| `--max-upload-size`   | `MAX_UPLOAD_SIZE`    | `MAX_UPLOAD_SIZE=64`                  |
| `--allow-root`        | `ALLOW_ROOT`         | `ALLOW_ROOT=1`                        |
| `--follow-symlinks`   | `FOLLOW_SYMLINKS`    | `FOLLOW_SYMLINKS=1`                   |

{% hint style="warning" %}
The boolean env vars (`ALLOW_EDITS`, `ALLOW_ROOT`, `FOLLOW_SYMLINKS`) are considered only when they are enabled, i.e. set to `1`. They cannot be used to deactivate a CLI parameter.
{% endhint %}
