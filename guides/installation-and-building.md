# 🏗 Installation & Building

### Installation

Installation consists of a single executable file. Head to the [releases](https://github.com/proofrock/pupcloud/releases) page on GitHub, and download the compressed file relevant for your OS and architecture; then extract it with a 7-zip compatible client.

If there are no files for your OS/arch, look into building it yourself, see below.

Either way, you'll have a single binary (albeit a little bulky). [Take it for a walk](running-pupcloud.md)!

#### Supported platforms

These are platforms for which I'll provide binaries at the time of the release.

| OS             | Arch    | Notes                                       |
| -------------- | ------- | ------------------------------------------- |
| Linux          | x86-64  | Static build for cross-distro compatibility |
| Linux          | armv7hf | Static build for cross-distro compatibility |
| Linux          | aarch64 | Static build for cross-distro compatibility |
| Windows        | x86-64  |                                             |
| MacOS (darwin) | x86-64  |                                             |

If you have access to an unsupported architecture, and would like to contribute the binary, please write me (oss /AT/ germanorizzo /DOT/ it).

### Building & Testing

#### Main app

Pupcloud is a Go(lang) program, that uses Go 1.18 and CGO (for a dependency). If you are not familiar with this, please read a guide on [compiling with CGO](https://go.dev/doc/install/gccgo); the Go toolset makes it very convenient, but there are some prerequisites.

* Go 1.18
* Make
* A compile toolchain (e.g. GCC)

I included a Make file to script the building under Linux/MacOS, so if you have all the prerequisites it should be a matter of:

```bash
git clone https://github.com/proofrock/pupcloud
cd pupcloud
make build # or build-static
# You will find the binary in the bin/ directory.
```

For MacOS replace Line 3 with:

```bash
make build
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
