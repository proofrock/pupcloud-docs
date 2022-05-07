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

| CLI Parameter         | Environment Variable  | Example                                   |
| --------------------- | --------------------- | ----------------------------------------- |
| `--root`, `-r`        | `PUP_ROOT`            | `PUP_ROOT=./`                             |
| `--bind-to`           | `PUP_BIND_TO`         | `PUP_BIND_TO=192.168.1.0`                 |
| `--port`, `-p`        | `PUP_PORT`            | `PUP_PORT=8080`                           |
| `--title`             | `PUP_TITLE`           | `PUP_TITLE=WowSite`                       |
| `--password`, `-P`    | `PUP_PASSWORD`        | `PUP_PASSWORD=ciao`                       |
| `--pwd-hash`, `-H`    | `PUP_PWD_HASH`        | `PUP_PWD_HASH=5302bf`                     |
| `--allow-edits`, `-E` | `PUP_ALLOW_EDITS`     | `PUP_ALLOW_EDITS=1`                       |
| `--share-profile`     | _nothing_             |                                           |
| `--share-profiles`    | `PUP_SHARE_PROFILES`  | `PUP_SHARE_PROFILES=k1:v1,k2:v2`          |
| `--share-prefix`      | `PUP_SHARE_PREFIX`    | `PUP_SHARE_PREFIX=http://localhost:12345` |
| `--share-port`        | `PUP_SHARE_PORT`      | `PUP_SHARE_PORT=12345`                    |
| `--max-upload-size`   | `PUP_MAX_UPLOAD_SIZE` | `PUP_MAX_UPLOAD_SIZE=64`                  |
| `--allow-root`        | `PUP_ALLOW_ROOT`      | `PUP_ALLOW_ROOT=1`                        |
| `--follow-symlinks`   | `PUP_FOLLOW_SYMLINKS` | `PUP_FOLLOW_SYMLINKS=1`                   |

{% hint style="warning" %}
The boolean env vars (`PUP_ALLOW_EDITS`, `PUP_ALLOW_ROOT`, `PUP_FOLLOW_SYMLINKS`) are considered only when they are enabled, i.e. set to `1`. They cannot be used to deactivate a CLI parameter.
{% endhint %}

### Write a "config file"

Pupcloud can't be configured with a config file. It's an explicit design choice, I wanted to limit all the "cruft" normally involved in installing an application... to the extreme. One day this might change though (see [Issue #20](https://github.com/proofrock/pupcloud/issues/20) for a short discussion).

For now, what _can_ be done is to use the env vars to build a shell script that looks like a config file; something like:

```bash
#!/bin/bash
export PUP_ROOT=/my/root
export PUP_ALLOW_EDITS=1
export PUP_PASSWORD=ciao
./pupcloud
```

or inline:

```bash
#!/bin/bash
PUP_ROOT=/my/root \
PUP_ALLOW_EDITS=1 \
PUP_PASSWORD=ciao \
./pupcloud
```
