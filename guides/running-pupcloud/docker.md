# 🐳 Docker

Official docker image available, for x86\_64 (amd64), arm and arm64 (aarch64). See [DockerHub's page](https://hub.docker.com/r/germanorizzo/pupcloud) for instructions.

### Docker image

The image is based on Alpine. It's a multiarch image for amd64, ARM and ARM64.

Here are the relevant configurations:

| Parameter    | Value            | Notes                     |
| ------------ | ---------------- | ------------------------- |
| Exposed port | `-p xxxx:17178`  | Fixed; remap it with `-p` |
| Config dir   | `-v [...]:/data` | Fixed; remap it with `-v` |
| User         | `-e PUID=1001`   | If not specified, 1000    |
| Group        | `-e PGID=1001`   | If not specified, 1000    |

Environment variables can be used to configure the various aspects of Pupcloud.

| Variable                                 | Help                                                                         |
| ---------------------------------------- | ---------------------------------------------------------------------------- |
| `-e TITLE="PupWow"`                      | Title of the window                                                          |
| `-e FOLLOW_SYMLINKS=1`                   | Follow symlinks when traversing directories                                  |
| `-e MAX_UPLOAD_SIZE=64`                  | The max size of an upload, in MiB                                            |
| `-e PASSWORD=ciao`                       | The main access password, if desired. Use --pwd-hash for a safer alternative |
| `-e PWD_HASH=5302bf`                     | SHA256 hash of the main access password, if desired                          |
| `-e READONLY=1`                          | Disallow all changes to FS                                                   |
| `-e SHARE_PORT=12345`                    | The port of the sharing interface                                            |
| `-e SHARE_PREFIX=http://localhost:12345` | The base URL of the sharing interface                                        |
| `-e SHARE_PROFILES=k1:v1,k2:v2`          | Profiles for sharing, in the form name:secret                                |

See [Running Pupcloud](./) for more info, and other variables (use with caution, the ones listed here are the "safe" ones).

#### Example

```bash
docker run -d \
 --restart=unless-stopped \
 --name=pupcloud \
 -p 8080:17178 \
 -v /mnt/DockerHome/myDir:/data \
 -e PID=1001 \
 -e PGID=1001 \
 -e TITLE="MyPupCloud!" \
 germanorizzo/pupcloud:latest
```

This command will install and run pupcloud, configuring it to:

* Use port 8080 (Line 4);
* Map a local dir to path `/data` in the docker environment (Line 5);
* Run the server as user/group 1001:1001 (Lines 6-7);
* Set the title (Line 8).

The rest of the lines in this example are standard Docker.

{% hint style="warning" %}
If you specify `FOLLOW_SYMLINKS`, please be aware that the links are resolved in the docker container, so the feature won't probably work. Use multiple bind/mounts inside `/data` instead.
{% endhint %}
