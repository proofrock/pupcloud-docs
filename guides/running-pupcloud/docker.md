# 🐳 Docker

Official docker image available, for x86\_64 (amd64), arm and arm64 (aarch64). See [DockerHub's page](https://hub.docker.com/r/germanorizzo/pupcloud) for instructions.

### Docker image

The image is based on Alpine. It's a multiarch image for amd64, ARM and ARM64.

Here are the relevant configurations:

| Parameter    | Value            | Notes                     |
| ------------ | ---------------- | ------------------------- |
| Exposed port | `-p xxxx:17178`  | Fixed; remap it with `-p` |
| Config dir   | `-v [...]:/data` | Fixed; remap it with `-v` |
| User         | `-e PUID=`       | If not specified, 1000    |
| Group        | `-e PGID=`       | If not specified, 1000    |

#### Example

```bash
docker run -d \
 --restart=unless-stopped \
 --name=pupcloud \
 -p 8080:17178 \
 -v /mnt/DockerHome/myDir:/data \
 -e PID=1001 \
 -e PGID=1001 \
 germanorizzo/pupcloud:latest \ 
 --title "MyPupCloud!"
```

This command will install and run pupcloud, configuring it to:

* Use port 8080 (Line 4);
* Map a local dir to path `/data` in the docker environment (Line 5);
* Run the server as user/group 1001:1001 (Lines 6-7);
* Use free cli arguments, as it was the pupcloud binary (Line 9).

The rest of the lines in this example are standard Docker.

{% hint style="warning" %}
**I**f you specify `--follow-symlinks`, please be aware that the links are resolved in the docker container, so the feature won't probably work. Use multiple bind/mounts inside `/data` instead.
{% endhint %}
