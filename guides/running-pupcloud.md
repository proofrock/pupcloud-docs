# 🏃♂ Running Pupcloud

Pupcloud is distributed as a single executable file. [Download and unpack the proper file for your OS/arch](installation-and-building.md#installation).

Once done, just execute it with the directory to serve as an argument:

```bash
pupcloud -r /my/dir
```

Then, open `http://localhost:17178` with a browser. As simple as that!

Run`pupcloud --help` to see the other configuration options:

```
Pupcloud v0.7.0 (c) 2022 Germano Rizzo
unknown shorthand flag: 'v' in -version
Usage of pupcloud:
      --allow-root                  Allow launching as root (default: don't)
      --bind-to string              The address to bind to (default "0.0.0.0")
      --follow-symlinks             Follow symlinks when traversing directories (default: don't)
      --max-upload-size int         The max size of an upload, in MiB (default 32)
  -P, --password string             The main access password, if desired. Use --pwd-hash for a safer alternative
  -p, --port int                    The port to run on (default 17178)
  -H, --pwd-hash string             SHA256 hash of the main access password, if desired
      --readonly                    Disallow all changes to FS (default: don't)
  -r, --root string                 The document root to serve
      --share-port int              The port of the sharing interface (default 17179)
      --share-prefix string         The base URL of the sharing interface (default: 'http://localhost:' + the port)
      --share-profile stringArray   Profile for sharing, in the form name:secret, multiple profiles allowed
      --title string                Title of the window (default "🐶 Pupcloud")
```

* disable all the write operations (`--readonly`);
* setup [authentication ](authentication.md)(`-P` or `-H`);
* setup [folder sharing](sharing-a-folder.md) (`--share-profile`, `--share-port`, `--share-prefix`)
* specify a title/header for the web UI page (`--title`);
* use a different port then the default of 17178 (`-p`);
* bind to a network interface (`--bind-to`);
* instruct pupcloud to follow symlinks (`--follow-symlinks`);
* specify a maximum size for upload, in Megabytes (`--max-upload-size`).

By default, it's forbidden to run it as root. Use `--allow-root` if you (really) want to.
