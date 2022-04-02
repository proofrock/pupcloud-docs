# 🏗 Installation & Building

### Installation

Installation consists of a single executable file. Head to the [releases](https://github.com/proofrock/pupcloud/releases) page on GitHub, and download the compressed file relevant for your OS and architecture; then extract it with a 7-zip compatible client.

If there are no files for your OS/arch, look into building it yourself, see below.

Either way, you'll have a single binary (albeit a little bulky). [Take it for a walk](running-pupcloud.md)!

#### Supported platforms

These are platforms for which I'll provide binaries at the time of the release.

| OS             | Arch  | Notes                                       |
| -------------- | ----- | ------------------------------------------- |
| Linux          | amd64 | Static build for cross-distro compatibility |
| Linux          | arm   | Static build for cross-distro compatibility |
| Linux          | arm64 | Static build for cross-distro compatibility |
| Windows        | amd64 |                                             |
| MacOS (darwin) | amd64 |                                             |
| MacOS (darwin) | arm64 |                                             |

Binaries are built using Go cross-compile capabilities, I don't have access to all the infrastructure needed to properly test all of them. Please report any inconsistency.

### Building & Testing

#### Main app

Pupcloud is a Go(lang) program, that uses Go 1.18. There are some basic prerequisites.

* Go 1.18
* Make

I included a Make file to script the building under Linux/MacOS, so if you have all the prerequisites it should be a matter of:

```bash
git clone https://github.com/proofrock/pupcloud
cd pupcloud
make build # or build-static, under Linux
# You will find the binary in the bin/ directory.
```

For Windows, instead of the step at Line 3 do:

```bash
cd src
go build
```

The sources include a precompiled version of the Web UI.

#### Web UI

If you want to rebuild the Web UI, you'll need also to install NodeJS and NPM. Then the command to use is:

```
make build-ui
```

This will build it and also copy the result to the proper directory where a `make build` will look for it and generate the binary.
